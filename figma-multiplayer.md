# Figma Multiplayer
First, let's start with what's OT (operational transformational)
## OT
OT was an algorithm developed by Google, which they used for Google Docs and other similar kinda editors also use it! It lets multiple users interact with a document at the same time, applying changes that provide consistency.
OT is an insert/delete-based algorithm, so if it has to update something, it deletes the existing one and inserts a new value. Although Figma decided not to use this algorithm for their multiplayer canvas.

## Why Figma decided not to go with OT??
OT would have introduced complexity for them as OT is an insert/delete-based algorithm. In Figma, there's not just linear text; the dataset they have to manage is more like a DOM structure we have in the web!
It goes something like this: frames -> documents -> shapes -> text -> groupings, etc.

So if they have used OT, it would have been so complex to manage things like bringing an object to the front; for this, they would have to delete all the parts in there and insert the order back again, or for the shape resizing, grouping objects, etc.

## What did they use instead?
A simple client-server model over a WebSocket layer, users download the file, then exchange incremental updates. Offline is supported by letting clients edit locally and replay changes on reconnect. Other data, like comments, teams, etc, lives in Postgres and syncs via a different pipeline.

Not sure about this, but their data model would be something like a map where they store object-ID and its properties like position, size, etc They use a CRDT inspired algorithm where they let a server decide what order of events will go through, and mostly the last write wins, and this all is incremental, so not insert/delete for an update.
This provides them consistency in the design, so if two users change the same rectangle size, the last event would come into place (This is something like LWW, last to reachthe  server, but it doesn't need to have a timestamp of changes)


## Operations 
- Creation and Deletion are as expected, for creating a new object client generates an ID for the object and then sends it tothe  server and for deletion, it simply deletes the object from the server, and the client saves the history for redos
- For Updates, the properties are just updated for the object
- Changing parents of the objects: All the data in the canvas is like a tree-based structure, so if we have a let's say frame on position-id 0 and over it a circle is there, so let's say its position-id is 1, now if for some reason we need to send this circle behind the frame, we'll change this parent-child order
- On a rectangle with position-id 0, and has 2 children A and B, both will have a fractional-based position like 0.5, 0.2.

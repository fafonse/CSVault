A method of designing/discussing complex systems by breaking up pieces/services into distinct *layers*.

Layers:
- Each layer implements a service
- Via it's own internal-layer actions
- Relying on the services provided by the layers below

## Why Layering?
- Explicit structure allows identification, relationship of system's pieces
	- Layered *reference model* for discussion
- Modularization eases maintenance, updating of system
	- Change in 1 layers *implementation* is "invisible" to the rest of the system
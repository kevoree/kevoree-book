# Known protocols
#### Kevoree groups WebSocket protocol
Kevoree uses Groups to share models between Node platforms. Each group has there own implementation and therefore uses its own protocol. In order to communicate with the groups, KWE uses the built-in Javascript WebSocket implementation available in modern Web browsers. Thus, your running Kevoree platform must have a compatible WebSocket group in order to communicate with KWE.

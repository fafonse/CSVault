HTTP is a web protocol primarily made for HTML. However, overtime we have made HTTP work with basically anything, so frameworks are now necessary for everything.

HTTP is an [[Layered Internet Protocol Stack|application layer]] protocol. It uses [[Transmission Control Protocol|TCP]] to get to the link layer.

## Persistent vs. Nonpersistent
Persistent
- TCP opened to a server
- multiple objects can be sent on a single TCP request

Nonpersistent
- TCP opened
- One object sent over the request

## Error Codes

- 404 - Page not found
- 301 - Document moved
- 200 - OK
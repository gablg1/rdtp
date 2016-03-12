# rdtp
Real Data Transfer Protocol. A super light weight socket transfer protocol that doesn't kill every connection like HTTP does.

# Usage

## Client

This assumes the client has a socket connected to a server. The general usage is

```rdtp.send(socket, status, arg0, arg1, ...)```

Arguments must be strings of size at most 256.

```
# Says hello to the server
rdtp.send(socket, 0, "hello", "world")
```

## Server

This assumes the server has a socket listening to the client. The general usage is

```status, args = rdtp.recv(socket)```

`status` is an int and `args` is a list of string arguments sent by `rdtp.send`

```
# Gets and prints a client message
status, args = rdtp.recv(socket)
if status != 0:
	print 'Something is wrong with the client'
else:
    # Print all args we got
	for arg in args:
		print arg


```

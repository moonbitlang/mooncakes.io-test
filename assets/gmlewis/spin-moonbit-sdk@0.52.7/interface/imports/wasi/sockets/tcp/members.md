# Documentation
|Type|description|
|---|---|
|[ShutdownType](#ShutdownType)||
|[TcpSocket](#TcpSocket)||

|Value|description|
|---|---|
|[ordinal](#ordinal)||

## ShutdownType

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,4:::pub(all) enum ShutdownType {
  RECEIVE
  SEND
  BOTH
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,8:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,8:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,8:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,8:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### from
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,20:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>::from(self : Int) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>
  ```
  > 
- #### ordinal
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,11:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>::ordinal(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>) -> Int
  ```
  > 

## TcpSocket

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,51:::pub(all) type TcpSocket Int
```

 A TCP socket resource.

 The socket can be in one of the following states:
 - `unbound`
 - `bind-in-progress`
 - `bound` (See note below)
 - `listen-in-progress`
 - `listening`
 - `connect-in-progress`
 - `connected`
 - `closed`
   See <https://github.com/WebAssembly/wasi-sockets/TcpSocketOperationalSemantics.md>
   for a more information.

 Note: Except where explicitly mentioned, whenever this documentation uses
the term "bound" without backticks it actually means: in the `bound` state *or higher*.
(i.e. `bound`, `listen-in-progress`, `listening`, `connect-in-progress` or `connected`)

 In addition to the general error codes documented on the
`network::error-code` type, TCP socket methods may always return
`error(invalid-state)` when in the `closed` state.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,51:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,51:::fn op_equal(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,51:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,51:::fn output(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### accept
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,417:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::accept(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams.InputStream</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams.OutputStream</a>), <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Accept a new client socket.
  > 
  >  The returned socket is bound and in the `connected` state. The following properties are inherited from the listener socket:
  >  - `address-family`
  >  - `keep-alive-enabled`
  >  - `keep-alive-idle-time`
  >  - `keep-alive-interval`
  >  - `keep-alive-count`
  >  - `hop-limit`
  >  - `receive-buffer-size`
  >  - `send-buffer-size`
  > 
  >  On success, this function returns the newly accepted client socket along with
  > a pair of streams that can be used to read & write to the connection.
  > 
  >  #### Typical errors
  >  - `invalid-state`:      Socket is not in the `listening` state. (EINVAL)
  >  - `would-block`:        No pending connections at the moment. (EWOULDBLOCK, EAGAIN)
  >  - `connection-aborted`: An incoming connection was pending, but was terminated by the client before this listener could accept it. (ECONNABORTED)
  >  - `new-socket-limit`:   The new socket resource could not be created because of a system limit. (EMFILE, ENFILE)
  > 
  >  #### References
  >  - <https://pubs.opengroup.org/onlinepubs/9699919799/functions/accept.html>
  >  - <https://man7.org/linux/man-pages/man2/accept.2.html>
  >  - <https://learn.microsoft.com/en-us/windows/win32/api/winsock2/nf-winsock2-accept>
  >  - <https://man.freebsd.org/cgi/man.cgi?query=accept&sektion=2>
- #### address\_family
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,581:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::address_family(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#IpAddressFamily">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.IpAddressFamily</a>
  ```
  > 
  >  Whether this is a IPv4 or IPv6 socket.
  > 
  >  Equivalent to the SO\_DOMAIN socket option.
- #### drop
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,57:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::drop(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> Unit
  ```
  > 
- #### finish\_bind
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,179:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::finish_bind(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### finish\_connect
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,315:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::finish_connect(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[(<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#InputStream">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams.InputStream</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams#OutputStream">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/streams.OutputStream</a>), <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### finish\_listen
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,376:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::finish_listen(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### hop\_limit
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,805:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::hop_limit(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Byte, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Equivalent to the IP\_TTL & IPV6\_UNICAST\_HOPS socket options.
  > 
  >  If the provided value is 0, an `invalid-argument` error is returned.
  > 
  >  #### Typical errors
  >  - `invalid-argument`:     (set) The TTL value must be 1 or higher.
- #### is\_listening
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,572:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::is_listening(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> Bool
  ```
  > 
  >  Whether the socket is in the `listening` state.
  > 
  >  Equivalent to the SO\_ACCEPTCONN socket option.
- #### keep\_alive\_count
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,764:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::keep_alive_count(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  The maximum amount of keepalive packets TCP should send before aborting the connection.
  > 
  >  If the provided value is 0, an `invalid-argument` error is returned.
  > Any other value will never cause an error, but it might be silently clamped and/or rounded.
  > I.e. after setting a value, reading the same setting back may return a different value.
  > 
  >  Equivalent to the TCP\_KEEPCNT socket option.
  > 
  >  #### Typical errors
  >  - `invalid-argument`:     (set) The provided value was 0.
- #### keep\_alive\_enabled
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,625:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::keep_alive_enabled(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Bool, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Enables or disables keepalive.
  > 
  >  The keepalive behavior can be adjusted using:
  >  - `keep-alive-idle-time`
  >  - `keep-alive-interval`
  >  - `keep-alive-count`
  >    These properties can be configured while `keep-alive-enabled` is false, but only come into effect when `keep-alive-enabled` is true.
  > 
  >  Equivalent to the SO\_KEEPALIVE socket option.
- #### keep\_alive\_idle\_time
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,674:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::keep_alive_idle_time(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Amount of time the connection has to be idle before TCP starts sending keepalive packets.
  > 
  >  If the provided value is 0, an `invalid-argument` error is returned.
  > Any other value will never cause an error, but it might be silently clamped and/or rounded.
  > I.e. after setting a value, reading the same setting back may return a different value.
  > 
  >  Equivalent to the TCP\_KEEPIDLE socket option. (TCP\_KEEPALIVE on MacOS)
  > 
  >  #### Typical errors
  >  - `invalid-argument`:     (set) The provided value was 0.
- #### keep\_alive\_interval
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,719:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::keep_alive_interval(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  The time between keepalive packets.
  > 
  >  If the provided value is 0, an `invalid-argument` error is returned.
  > Any other value will never cause an error, but it might be silently clamped and/or rounded.
  > I.e. after setting a value, reading the same setting back may return a different value.
  > 
  >  Equivalent to the TCP\_KEEPINTVL socket option.
  > 
  >  #### Typical errors
  >  - `invalid-argument`:     (set) The provided value was 0.
- #### local\_address
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,459:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::local_address(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#IpSocketAddress">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.IpSocketAddress</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Get the bound local address.
  > 
  >  POSIX mentions:
  >  > If the socket has not been bound to a local name, the value
  >  > stored in the object pointed to by `address` is unspecified.
  > 
  >  WASI is stricter and requires `local-address` to return `invalid-state` when the socket hasn't been bound yet.
  > 
  >  #### Typical errors
  >  - `invalid-state`: The socket is not bound to any local address.
  > 
  >  #### References
  >  - <https://pubs.opengroup.org/onlinepubs/9699919799/functions/getsockname.html>
  >  - <https://man7.org/linux/man-pages/man2/getsockname.2.html>
  >  - <https://learn.microsoft.com/en-us/windows/win32/api/winsock/nf-winsock-getsockname>
  >  - <https://man.freebsd.org/cgi/man.cgi?getsockname>
- #### receive\_buffer\_size
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,846:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::receive_buffer_size(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  The kernel buffer space reserved for sends/receives on this socket.
  > 
  >  If the provided value is 0, an `invalid-argument` error is returned.
  > Any other value will never cause an error, but it might be silently clamped and/or rounded.
  > I.e. after setting a value, reading the same setting back may return a different value.
  > 
  >  Equivalent to the SO\_RCVBUF and SO\_SNDBUF socket options.
  > 
  >  #### Typical errors
  >  - `invalid-argument`:     (set) The provided value was 0.
- #### remote\_address
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,519:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::remote_address(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[<a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#IpSocketAddress">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.IpSocketAddress</a>, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Get the remote address.
  > 
  >  #### Typical errors
  >  - `invalid-state`: The socket is not connected to a remote address. (ENOTCONN)
  > 
  >  #### References
  >  - <https://pubs.opengroup.org/onlinepubs/9699919799/functions/getpeername.html>
  >  - <https://man7.org/linux/man-pages/man2/getpeername.2.html>
  >  - <https://learn.microsoft.com/en-us/windows/win32/api/winsock/nf-winsock-getpeername>
  >  - <https://man.freebsd.org/cgi/man.cgi?query=getpeername&sektion=2&n=1>
- #### send\_buffer\_size
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,881:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::send_buffer_size(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[UInt64, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### set\_hop\_limit
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,820:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_hop_limit(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : Byte) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### set\_keep\_alive\_count
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,779:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_keep_alive_count(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : UInt) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### set\_keep\_alive\_enabled
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,640:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_keep_alive_enabled(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : Bool) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### set\_keep\_alive\_idle\_time
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,689:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_keep_alive_idle_time(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### set\_keep\_alive\_interval
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,734:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_keep_alive_interval(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### set\_listen\_backlog\_size
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,596:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_listen_backlog_size(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Hints the desired listen queue size. Implementations are free to ignore this.
  > 
  >  If the provided value is 0, an `invalid-argument` error is returned.
  > Any other value will never cause an error, but it might be silently clamped and/or rounded.
  > 
  >  #### Typical errors
  >  - `not-supported`:        (set) The platform does not support changing the backlog size after the initial listen.
  >  - `invalid-argument`:     (set) The provided value was 0.
  >  - `invalid-state`:        (set) The socket is in the `connect-in-progress` or `connected` state.
- #### set\_receive\_buffer\_size
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,861:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_receive_buffer_size(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### set\_send\_buffer\_size
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,896:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::set_send_buffer_size(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, value : UInt64) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
- #### shutdown
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,962:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::shutdown(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, shutdown_type : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Initiate a graceful shutdown.
  > 
  >  - `receive`: The socket is not expecting to receive any data from
  >    the peer. The `input-stream` associated with this socket will be
  >    closed. Any data still in the receive queue at time of calling
  >    this method will be discarded.
  >  - `send`: The socket has no more data to send to the peer. The `output-stream`
  >    associated with this socket will be closed and a FIN packet will be sent.
  >  - `both`: Same effect as `receive` & `send` combined.
  > 
  >  This function is idempotent. Shutting a down a direction more than once
  > has no effect and returns `ok`.
  > 
  >  The shutdown function does not close (drop) the socket.
  > 
  >  #### Typical errors
  >  - `invalid-state`: The socket is not in the `connected` state. (ENOTCONN)
  > 
  >  #### References
  >  - <https://pubs.opengroup.org/onlinepubs/9699919799/functions/shutdown.html>
  >  - <https://man7.org/linux/man-pages/man2/shutdown.2.html>
  >  - <https://learn.microsoft.com/en-us/windows/win32/api/winsock/nf-winsock-shutdown>
  >  - <https://man.freebsd.org/cgi/man.cgi?query=shutdown&sektion=2>
- #### start\_bind
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,100:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::start_bind(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, network : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#Network">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.Network</a>, local_address : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#IpSocketAddress">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.IpSocketAddress</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Bind the socket to a specific network on the provided IP address and port.
  > 
  >  If the IP address is zero (`0.0.0.0` in IPv4, `::` in IPv6), it is left to the implementation to decide which
  > network interface(s) to bind to.
  > If the TCP/UDP port is zero, the socket will be bound to a random free port.
  > 
  >  Bind can be attempted multiple times on the same socket, even with
  > different arguments on each iteration. But never concurrently and
  > only as long as the previous bind failed. Once a bind succeeds, the
  > binding can't be changed anymore.
  > 
  >  #### Typical errors
  >  - `invalid-argument`:          The `local-address` has the wrong address family. (EAFNOSUPPORT, EFAULT on Windows)
  >  - `invalid-argument`:          `local-address` is not a unicast address. (EINVAL)
  >  - `invalid-argument`:          `local-address` is an IPv4-mapped IPv6 address. (EINVAL)
  >  - `invalid-state`:             The socket is already bound. (EINVAL)
  >  - `address-in-use`:            No ephemeral ports available. (EADDRINUSE, ENOBUFS on Windows)
  >  - `address-in-use`:            Address is already in use. (EADDRINUSE)
  >  - `address-not-bindable`:      `local-address` is not an address that the `network` can bind to. (EADDRNOTAVAIL)
  >  - `not-in-progress`:           A `bind` operation is not in progress.
  >  - `would-block`:               Can't finish the operation, it is still in progress. (EWOULDBLOCK, EAGAIN)
  > 
  >  #### Implementors note
  >  When binding to a non-zero port, this bind operation shouldn't be affected by the TIME\_WAIT
  > state of a recently closed socket on the same local address. In practice this means that the SO\_REUSEADDR
  > socket option should be set implicitly on all platforms, except on Windows where this is the default behavior
  > and SO\_REUSEADDR performs something different entirely.
  > 
  >  Unlike in POSIX, in WASI the bind operation is async. This enables
  > interactive WASI hosts to inject permission prompts. Runtimes that
  > don't want to make use of this ability can simply call the native
  > `bind` as part of either `start-bind` or `finish-bind`.
  > 
  >  #### References
  >  - <https://pubs.opengroup.org/onlinepubs/9699919799/functions/bind.html>
  >  - <https://man7.org/linux/man-pages/man2/bind.2.html>
  >  - <https://learn.microsoft.com/en-us/windows/win32/api/winsock/nf-winsock-bind>
  >  - <https://man.freebsd.org/cgi/man.cgi?query=bind&sektion=2&format=html>
- #### start\_connect
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,236:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::start_connect(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>, network : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#Network">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.Network</a>, remote_address : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#IpSocketAddress">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.IpSocketAddress</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Connect to a remote endpoint.
  > 
  >  On success:
  >  - the socket is transitioned into the `connection` state.
  >  - a pair of streams is returned that can be used to read & write to the connection
  > 
  >  After a failed connection attempt, the socket will be in the `closed`
  > state and the only valid action left is to `drop` the socket. A single
  > socket can not be used to connect more than once.
  > 
  >  #### Typical errors
  >  - `invalid-argument`:          The `remote-address` has the wrong address family. (EAFNOSUPPORT)
  >  - `invalid-argument`:          `remote-address` is not a unicast address. (EINVAL, ENETUNREACH on Linux, EAFNOSUPPORT on MacOS)
  >  - `invalid-argument`:          `remote-address` is an IPv4-mapped IPv6 address. (EINVAL, EADDRNOTAVAIL on Illumos)
  >  - `invalid-argument`:          The IP address in `remote-address` is set to INADDR\_ANY (`0.0.0.0` / `::`). (EADDRNOTAVAIL on Windows)
  >  - `invalid-argument`:          The port in `remote-address` is set to 0. (EADDRNOTAVAIL on Windows)
  >  - `invalid-argument`:          The socket is already attached to a different network. The `network` passed to `connect` must be identical to the one passed to `bind`.
  >  - `invalid-state`:             The socket is already in the `connected` state. (EISCONN)
  >  - `invalid-state`:             The socket is already in the `listening` state. (EOPNOTSUPP, EINVAL on Windows)
  >  - `timeout`:                   Connection timed out. (ETIMEDOUT)
  >  - `connection-refused`:        The connection was forcefully rejected. (ECONNREFUSED)
  >  - `connection-reset`:          The connection was reset. (ECONNRESET)
  >  - `connection-aborted`:        The connection was aborted. (ECONNABORTED)
  >  - `remote-unreachable`:        The remote address is not reachable. (EHOSTUNREACH, EHOSTDOWN, ENETUNREACH, ENETDOWN, ENONET)
  >  - `address-in-use`:            Tried to perform an implicit bind, but there were no ephemeral ports available. (EADDRINUSE, EADDRNOTAVAIL on Linux, EAGAIN on BSD)
  >  - `not-in-progress`:           A connect operation is not in progress.
  >  - `would-block`:               Can't finish the operation, it is still in progress. (EWOULDBLOCK, EAGAIN)
  > 
  >  #### Implementors note
  >  The POSIX equivalent of `start-connect` is the regular `connect` syscall.
  > Because all WASI sockets are non-blocking this is expected to return
  > EINPROGRESS, which should be translated to `ok()` in WASI.
  > 
  >  The POSIX equivalent of `finish-connect` is a `poll` for event `POLLOUT`
  > with a timeout of 0 on the socket descriptor. Followed by a check for
  > the `SO_ERROR` socket option, in case the poll signaled readiness.
  > 
  >  #### References
  >  - <https://pubs.opengroup.org/onlinepubs/9699919799/functions/connect.html>
  >  - <https://man7.org/linux/man-pages/man2/connect.2.html>
  >  - <https://learn.microsoft.com/en-us/windows/win32/api/winsock2/nf-winsock2-connect>
  >  - <https://man.freebsd.org/cgi/man.cgi?connect>
- #### start\_listen
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,361:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::start_listen(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="moonbitlang/core/result#Result">Result</a>[Unit, <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network#ErrorCode">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/network.ErrorCode</a>]
  ```
  > 
  >  Start listening for new connections.
  > 
  >  Transitions the socket into the `listening` state.
  > 
  >  Unlike POSIX, the socket must already be explicitly bound.
  > 
  >  #### Typical errors
  >  - `invalid-state`:             The socket is not bound to any local address. (EDESTADDRREQ)
  >  - `invalid-state`:             The socket is already in the `connected` state. (EISCONN, EINVAL on BSD)
  >  - `invalid-state`:             The socket is already in the `listening` state.
  >  - `address-in-use`:            Tried to perform an implicit bind, but there were no ephemeral ports available. (EADDRINUSE)
  >  - `not-in-progress`:           A listen operation is not in progress.
  >  - `would-block`:               Can't finish the operation, it is still in progress. (EWOULDBLOCK, EAGAIN)
  > 
  >  #### Implementors note
  >  Unlike in POSIX, in WASI the listen operation is async. This enables
  > interactive WASI hosts to inject permission prompts. Runtimes that
  > don't want to make use of this ability can simply call the native
  > `listen` as part of either `start-listen` or `finish-listen`.
  > 
  >  #### References
  >  - <https://pubs.opengroup.org/onlinepubs/9699919799/functions/listen.html>
  >  - <https://man7.org/linux/man-pages/man2/listen.2.html>
  >  - <https://learn.microsoft.com/en-us/windows/win32/api/winsock2/nf-winsock2-listen>
  >  - <https://man.freebsd.org/cgi/man.cgi?query=listen&sektion=2>
- #### subscribe
  ```moonbit
  :::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,933:::fn <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>::subscribe(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#TcpSocket">TcpSocket</a>) -> <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll#Pollable">@gmlewis/spin-moonbit-sdk/interface/imports/wasi/io/poll.Pollable</a>
  ```
  > 
  >  Create a `pollable` which can be used to poll for, or block on,
  > completion of any of the asynchronous operations of this socket.
  > 
  >  When `finish-bind`, `finish-listen`, `finish-connect` or `accept`
  > return `error(would-block)`, this pollable can be used to wait for
  > their success or failure, after which the method can be retried.
  > 
  >  The pollable is not limited to the async operation that happens to be
  > in progress at the time of calling `subscribe` (if any). Theoretically,
  > `subscribe` only has to be called once per socket and can then be
  > (re)used for the remainder of the socket's lifetime.
  > 
  >  See <https://github.com/WebAssembly/wasi-sockets/TcpSocketOperationalSemantics.md#Pollable-readiness>
  > for a more information.
  > 
  >  Note: this function is here for WASI Preview2 only.
  > It's planned to be removed when `future` is natively supported in Preview3.

## ordinal

```moonbit
:::source,gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp/top.mbt,11:::fn ordinal(self : <a href="gmlewis/spin-moonbit-sdk/interface/imports/wasi/sockets/tcp#ShutdownType">ShutdownType</a>) -> Int
```


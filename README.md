# API Documentation for bacloud

## Headers

<table>
<tr>
<th>Request</th>
<th>Response</th>
</tr>
<tr>
<td>

```http
POST https://ballistica.net/bacloudcmd
Host: ballistica.net
User-Agent: bacloud/7
Accept-Encoding: gzip, deflate
Accept: */*
Connection: keep-alive
Content-Length: 128
Content-Type: application/x-www-form-urlencoded
```

</td>
<td>

```http
200 OK
content-type: text/html; charset=utf-8
vary: Accept-Encoding
Content-Encoding: gzip
X-Cloud-Trace-Context: 55555555555555555555555555555555
Date: Fri, 08 Jul 2022 12:04:41 GMT
Server: Google Frontend
Cache-Control: private
Transfer-Encoding: chunked
```

</td>
</tr>
</table>

## Data

<table>
<tr>
<th>Request</th>
<th>Response</th>
<th>Comments</th>
</tr>
<tr>
<td>

```json
v: 7
r: {
  "c": "user",
  "t": null,
  "p": {
    "a": ["login"]
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "\u001b[34mAuthenticating via web-browser...\u001b[0m",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": "https://ballistica.net?loginproxy=113377",
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": [
    "login_progress",
    {
      "s": [2022, 7, 8, 12, 4, 41, 748400],
      "c": 0,
      "p": "113377",
      "k": "5ca1ab1e-cafe-f00d-fea7-deadf007ba11"
    }
  ]
}
```

</td>
<td>

Initiate Login process. Send `end_command` next
</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "login_progress",
  "t": null,
  "p": {
    "s": [2022, 7, 8, 12, 4, 41, 748400],
    "c": 0,
    "p": "113377",
    "k": "5ca1ab1e-cafe-f00d-fea7-deadf007ba11"
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": null,
  "message_end": "\n",
  "error": null,
  "delay_seconds": 1.0,
  "login": null,
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": null,
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": [
    "login_progress",
    {
      "s": [2022, 7, 8, 12, 4, 41, 748400],
      "c": 1,
      "p": "113377",
      "k": "5ca1ab1e-cafe-f00d-fea7-deadf007ba11"
    }
  ]
}
```

</td>
<td>

Poll the server for Login completion.

The user has not yet logged in.

Poll again with `end_command` after `delay_seconds`
</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "login_progress",
  "t": null,
  "p": {
    "s": [2022, 7, 8, 12, 4, 41, 748400],
    "c": 1,
    "p": "113377",
    "k": "5ca1ab1e-cafe-f00d-fea7-deadf007ba11"
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "\u001b[94mLogging in...\u001b[0m",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": "b2hub19pX2dvdF9wd25k",
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": null,
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": [
    "login_finish",
    {
      "proxyid": "113377",
      "aname": "aryan02420"
    }
  ]
}
```

</td>
<td>

Poll the server for Login completion.

The client has logged in.

Save the login token for all future requests. Send `login_finish` command.
</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "login_finish",
  "t": "b2hub19pX2dvdF9wd25k",
  "p": {
    "proxyid": "113377",
    "aname": "aryan02420"
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "\u001b[92mYou are now logged in as \u001b[1maryan02420\u001b[0m\u001b[92m.\u001b[0m",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": null,
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": null
}
```

</td>
<td>

Indicate successful login to the server.
(to free up proxyids?)
</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "user",
  "t": "b2hub19pX2dvdF9wd25k",
  "p": {
    "a": ["status"]
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "Logged in as \u001b[92maryan02420\u001b[0m.",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": null,
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": null
}
```

</td>
<td>

Check login status. Note the token stored earlier is sent here.
</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "user",
  "t": "b2hub19pX2dvdF9wd25k",
  "p": {
    "a": ["logout"]
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "\u001b[92mYou are now logged out.\u001b[0m",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": true,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": null,
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": null
}
```

</td>
<td>

Successful logout. Discard the login token.
</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "user",
  "t": null,
  "p": {
    "a": ["status"]
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "Not logged in.",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": null,
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": null
}
```

</td>
<td>

User status when not logged in.
</td>
</tr>
</table>

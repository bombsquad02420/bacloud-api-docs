# API Documentation for bacloud

Reversed from [`tools/bacloud`](#) and Network interception

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

<tr>
<td>

```json
v: 7
r: {
  "c": "user",
  "t": "b2hub19pX2dvdF9wd25k",
  "p": {
    "a": ["workspace"]
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "...",
  "message_end": "\n",
  "error": "",
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

`bacloud workspace`

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
    "a": ["workspace", "list"]
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "1: \u001b[34mWorkspace1\u001b[0m\n",
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

`bcloud workspace list`

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
    "a": ["workspace", "get"]
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
  "error": "Expected workspace name and local path.",
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

`bcloud workspace get`

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
    "a": ["workspace", "get"]
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
  "error": "Expected workspace name and local path.",
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

`bcloud workspace get Workspace1`

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
    "a": ["workspace", "get"]
  },
  "z": 0.0,
  "y": true
}
```

</td>
<td>

```json
{
  "message": "Syncing \u001b[94m\u001b[1mWorkspace1\u001b[0m from the cloud to \u001b[94m./localws/Workspace1\u001b[0m...",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": "./localws/Workspace1",
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
    "workspace_get_process",
    {
      "workspace_name": "Workspace1",
      "workspace_dir": "./localws/Workspace1",
      "manifest": {
        "f": {},
        "_empty_hash": null
      },
      "p": 0,
      "total_deletes": 0,
      "total_dls": 0,
      "total_unmodified": null
    }
  ]
}
```

</td>
<td>

`bcloud workspace get Workspace1 ./localws`

</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "workspace_get_process",
  "t": "b2hub19pX2dvdF9wd25k",
  "p": {
    "workspace_name": "Workspace1",
    "workspace_dir": "./localws/Workspace1",
    "manifest": {
      "f": {},
      "_empty_hash": null
    },
    "p": 0,
    "total_deletes": 0,
    "total_dls": 0,
    "total_unmodified": null
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
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": null,
  "deletes": [],
  "downloads_inline": {
    "./localws/Workspace1/test.py": "eJxljzFvhDAMhff8Ch833CEVGCvd0LHqclWH25HhDERNYmqHUv59A1RVpXqx5ff85cUc4UbOQRwIZhZ3h3mw7QCfJGo5AHebhOMIc2qSXGJjpAAdy8UcocHaU0QQ+pisrE4Lj2l/Y3CEEsCz0AMoEQwxjnqpqgadsxpti2WgWM323VYro4jYF7poJG+M9SNLTHhj/kXEhqcIPAm8uam34W8O+truxk0wpnWoCtdlN54bLPcpvxhIlWXZdQGcSdnTz1GZlmZT79QBhzp9vpYpBBv6s5Lrciie4JUD7Yy1EldbIQqeVLGn8+klRWZ4Fva/rx8Oh1O+k78BD796Yw=="
  },
  "dir_prune_empty": "./localws/Workspace1",
  "open_url": null,
  "input_prompt": null,
  "end_message": "\u001b[32mSync complete. 1 files downloaded.\u001b[0m",
  "end_message_end": "\n",
  "end_command": null
}
```

</td>
<td>

``

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
    "a": ["workspace", "put"]
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
  "error": "Expected one path arg.",
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

`bacloud workspace put`

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
    "a": ["workspace", "put", "./localws/nodir"]
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
  "error": "Workspace with name 'nodir' not found for this account.",
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

`bacloud workspace put ./localws/nodir`

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
    "a": ["workspace", "put", "./localws/Workspace1"]
  },
  "z": 0.0,
  "y": true
}

```

</td>
<td>

```json
{
  "message": "Syncing \u001b[94m./localws/Workspace1\u001b[0m to the cloud as \u001b[94m\u001b[1mWorkspace1\u001b[0m...",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": "./localws/Workspace1",
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
    "workspace_putprocess",
    {
      "workspaceid": "8ekW6HdPWRmEMq8PGwrH",
      "workspacepath": "./localws/Workspace1",
      "manifest": {
        "f": {},
        "_empty_hash": null,
      },
      "uploads_inline": {},
    }
  ]
}
```

</td>
<td>

`bacloud workspace put ./localws/Workspace1`

</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "workspace_putprocess",
  "t": "rigRJIhoezsBtjUEIrGy",
  "p": {
    "workspaceid": "8ekW6HdPWRmEMq8PGwrH",
    "workspacepath": "./localws/Workspace1",
    "manifest": {
      "f": {
        "test.py": {
          "h": "cc1a91336a95a9ed50e7889ac3904174fcac7da93dee6f05718fffa3ce6e6a36",
          "s": 197
        }
      },
      "_empty_hash": null
    },
    "uploads_inline": {}
  },
  "z": 0.0,
  "y": true
}

```

</td>
<td>

```json
{
  "message": "Uploading 1 file(s)...",
  "message_end": "\n",
  "error": null,
  "delay_seconds": 0.0,
  "login": null,
  "logout": false,
  "dir_manifest": null,
  "uploads": null,
  "uploads_inline": [
    "./localws/Workspace1/test.py"
  ],
  "deletes": null,
  "downloads_inline": null,
  "dir_prune_empty": null,
  "open_url": null,
  "input_prompt": null,
  "end_message": null,
  "end_message_end": "\n",
  "end_command": [
    "workspace_putprocess",
    {
    "manifest": {
    "_empty_hash": null,
    "f": {
    "test.py": {
    "h": "cc1a91336a95a9ed50e7889ac3904174fcac7da93dee6f05718fffa3ce6e6a36",
    "s": 197
    }
    }
    },
    "uploads_inline": {},
    "workspaceid": "8ekW6HdPWRmEMq8PGwrH",
    "workspacepath": "./localws/Workspace1"
    }
  ],
}
```

</td>
<td>

``

</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "",
  "t": "b2hub19pX2dvdF9wd25k",
  "p": {},
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

``

</td>
</tr>

<tr>
<td>

```json
v: 7
r: {
  "c": "",
  "t": "b2hub19pX2dvdF9wd25k",
  "p": {},
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

``

</td>
</tr>
</table>

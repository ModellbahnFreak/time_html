# Time.html
This is a simple HTML page that displays the current time and delta time to a custom timestamp in the browser.

It can use the time of the local machine or the (roughly) round trip time compensated time from a server

## Installation
1. Serve the time.html file using ANY web-server on any url/path you like
1. If you want server time support:
    - With nginx: Paste the snippet from `nginx_server.conf` into your `server {...}` block of your nginx config
    - With other server: Serve a unix-timestamp (more precission via float supported) on the url `/server_time` on the same sub-path as the `time.html` file. (e.g. example.com/time and example.com/server_time or example.com/some/sub/path/time.html and example.com/some/sub/path/server_time)

## URL-Parameters/Settings
All settings can be changed using the UI. In this case they will be stored in the localStorage of the browser.

They can also be set using url search parameters (values in brackets of heading). These will take precedence over stored settings but won't overwrite them.

### Use UTS-Time (`utc=[false/true]`)
- Changes whether to display the local timesone of the machine or UTC time
- Will reflect in the timestamp format

### Dark design (`dark=[true/false]`)
- If off: Use black text on white background
- If on: Use white text on black background

### Use server time (`serverTime=[true/false]`)
- Only available if server_time is available
- Displays the time the server provided instead of the local machine time

### Destination/Delta time (`dstTime=[ISO-Timestamp]`)
- The time to which to count down to/up from in the "delta time" part

### Fullscreen (`fullscreen=[currTime/deltaTime/all]`)
- The part of the page to maximize/put into fulscreen mode
- &#x26f6; Maximizes the element AND puts the browser into fulscreen mode
- &#x21f1; Maximizes the element only
- Exit fullscreen as specified by browser
- Exit maximized mode using "Esc" or by removing the url parameter from the url

## Local testing
For local testing without a (proper) webserver there is a `server_time` text file in this directory. If you use a tool like [http-server](https://www.npmjs.com/package/http-server) for development, the `time.html` page will assume the contents of this file to be the "server time". That way you can test offsets etc.
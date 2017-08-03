# Debugging any Browser that does not have support for remote debugging
- Debug Android Stock Browser
- Debug IOS/Apple phones and tablets
- Simply debug in any browser. :)


How-to guide in debugging any mobile browser that does not have a good debug tool.

If your local website can be exposed to your device, you don't need install the Ngrok.

## Step-by-step

- Install the weinre app: `sudo npm -g install weinre` 
- After that, You can start it typing: `weinre`

If you are not able to expose your machine's ip, try using ngrok.

You can download it here: 
- [Mac](https://dl.ngrok.com/darwin_amd64/ngrok.zip)
- [Linux](https://dl.ngrok.com/linux_386/ngrok.zip)
- [Windows](https://dl.ngrok.com/windows_386/ngrok.zip)
- [Other plataforms](https://ngrok.com/)


- Unzip it: `$ unzip /path/to/ngrok.zip`
- Make a file `~/.ngrok2/.ngrok.yml` with this content:

```
authtoken: <YOUR-TOKEN>
tunnels:
  debug:
    proto: http
    addr: 8080
  project:
    proto: http
    addr: 9000
```

- Replace `<YOUR-TOKEN>` by the token generated in `http://ngrok.com` after signing up.
- Serve your web page trough the port 9000 `php -S localhost:9000`
- Run it: `$ ./ngrok start --all`
- Open in your machine the url `http://localhost:8080` to access the debug tool
- Change the weinre script tag to `<script src="<address_given_by_ngrok_for_debug_tunnel>/target/target-script-min.js#anonymous"></script>`
- Access your website using the alias on the Android stock browser 
- Enjoy!

## References:

- https://ngrok.com/
- http://www.broken-links.com/2013/06/28/remote-debugging-with-weinre/
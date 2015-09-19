curlIE is an implementation of a subset of the [cURL](http://curl.haxx.se/) command line interface in JavaScript using the XMLHttpRequest object in the [Microsoft Windows Script Host environment](http://msdn.microsoft.com/en-us/library/9bbdkx3k.aspx).

This tool will help you to retrieve remote files from a DOS prompt or in batch files.

<wiki:gadget title="SVN log" url="http://google-code-project-hosting-gadgets.googlecode.com/svn/build/prod/changes/gcChanges.xml" up\_projectName="curlie" up\_path="/trunk/curlIE.wsf"/>

## Features ##
  * easier to install than cURL on Windows platforms (one single file to download) in particular when you want to access HTTPS sites
  * uses the Microsoft Internet HTTP engine, so uses all Internet Explorer settings:
    * if IE passes the proxy, curlIE will too
    * uses IE cookies repository
    * transparent gzip compression
    * uses Windows SSL certificates, like IE:
      * no need to [build](https://github.com/bagder/curl/blob/master/lib/mk-ca-bundle.vbs) and keep up-to-date a `ca-bundle.crt` file as must be done for cURL.
      * if certificates are updated by Windows Update, curlIE is updated too
      * same certificates as in IE, no more, no less. As trust is the key in SSL, you can trust curlIE as much as IE.

curlIE is also an example of using the XMLHttpRequest object outside the browser context.

## Limitations ##
Due to limitations of WSH all cURL features can not be implemented:
  * WSH is limited to text output on STDOUT, so binary data can not be retrieved on this stream. Use the `-o` option instead to output to a file.
  * `-k`/`--insecure` can not be implemented.

## Download ##

You can download the latest version [here](http://curlie.googlecode.com/svn/trunk/curlIE.wsf) (right click, _Save file as..._)

To upgrade, see examples below or use the `--self-upgrade` command (requires version 1.008).

## Examples ##
curlie command line usage:
```
cscript //NoLogo curlie.wsf --help
```

Update curlIE:
```
cscript //NoLogo curlie.wsf -o curlIE.wsf http://curlie.googlecode.com/svn/trunk/curlIE.wsf
```
_Note: starting from version 1.008, curlIE has also the `--self-upgrade` command._

Download an image:
```
cscript //NoLogo curlie.wsf -o google.ico http://www.google.com/favicon.ico
```

## Tips ##
To simplify curlIE usage and WSH usage in general you can change WSH default settings like this:
```
cscript //NoLogo //H:CScript //S
```
You can now simply call the curlIE script without "cscript" and without the extension:
```
curlIE --help
```

## History ##
[History](History.md)
# Lighttpd config file
It took me a while to get lighttpd properly configured with all the various docs/guides so different from one another. So I wanted to save it in a good place. This is for lighttpd version 1.4.50

```
# Server options should be set outside of host conditionals

server.port = 80
server.username = "http"
server.groupname = "http"
server.errorlog = "/var/log/lighttpd/error.log"

# Servers document-root should have a global default but also be set for each host
server.document-root = "/var/www/default/dist"


$HTTP["host"] =~ "(^|\.)example1\.com$" {
	server.document-root	= "/var/www/example1/dist"
	dir-listing.activate  = "enable"
	index-file.names      = ( "index.html" )
	mimetype.assign       = (
				".html" => "text/html",
				".txt" => "text/plain",
				".css" => "text/css",
				".js" => "application/x-javascript",
				".jpg" => "image/jpeg",
				".jpeg" => "image/jpeg",
				".gif" => "image/gif",
				".png" => "image/png",
				"" => "application/octet-stream"
				)
}
$HTTP["host"] =~ "(^|\.)example2\.com$" {
	server.document-root  = "/var/www/example2/dist"
	dir-listing.activate  = "enable"
	index-file.names      = ( "index.html" )
	mimetype.assign       = (
				".html" => "text/html",
				".txt" => "text/plain",
				".css" => "text/css",
				".js" => "application/x-javascript",
				".jpg" => "image/jpeg",
				".jpeg" => "image/jpeg",
				".gif" => "image/gif",
				".png" => "image/png",
				"" => "application/octet-stream"
				)
}
```

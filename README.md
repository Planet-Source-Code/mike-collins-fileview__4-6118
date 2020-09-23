<div align="center">

## FileView


</div>

### Description

Ever get those annoying ASP error codes?

Wish you could see the line in question?

FileView.ASP allows you to see the line of code that is at fault
 
### More Info
 
fileview.asp?file=[filename]&line=[linenumber]

Diplays the file with the selected line highlighted.

None that I know if.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mike Collins](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mike-collins.md)
**Level**          |Intermediate
**User Rating**    |3.7 (11 globes from 3 users)
**Compatibility**  |ASP \(Active Server Pages\)
**Category**       |[Debugging and Error Handling](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/debugging-and-error-handling__4-6.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mike-collins-fileview__4-6118/archive/master.zip)

### API Declarations

Copyright (c) 2000 Mike Collins


### Source Code

```
<%@ LANGUAGE=JSCRIPT %>
<%Response.Buffer = true;%>
<%
Response.AddHeader( "content-type",
  "text/html; charset=UTF-8" );
Response.AddHeader( "cache-control",
  "no-cache" );
Response.Expires = 0;
var fileName = new String( ""+Request( "file" ) );
var line = new Number( ""+Request( "line" ) );
var fso = Server.CreateObject( "Scripting.FileSystemObject" );
var iFile = fso.OpenTextFile(
 Server.MapPath( fileName ), 1, false, 0 );
var i = 1;
%>
<html>
<head>
<title>File View page</title>
<style>
body, td { font: 8pt Courier; }
.blackbg { font-weight: bold; background: #000000; color:#FFFFFF; }
</style>
</head>
<body>
<table cellpadding="3" cellspacing="0">
<%
while( !iFile.AtEndOfStream )
{
 Response.Write( "<tr" );
 if( i == line )
 {
  Response.Write(" bgcolor=\"#FFCCCC\"");
 } else
 if( i & 1 )
 {
  Response.Write(" bgcolor=\"#FFFFEE\"");
 }
 Response.Write("><td align=\"right\"><b>");
 Response.Write(i+"</b></td><td nowrap>");
 Response.Write(Server.HTMLEncode(
  iFile.ReadLine() )+"</td></tr>\r\n" );
 i++;
}
iFile.Close();
%>
</table>
</body>
</html>
```


# PDF Service

The `PDF service` is easy to use.

![alt text](pdf_service.png)

If we intercept the request, we can show an error with `pdfTeX Version 3.14`.

![alt text](burp_error.png)

Only the `second template` works and creates pdf. We can inject this payload on the content to get an `RCE exploit` :  `\immediate\write18{command}`

![alt text](RCE.png)

![alt text](rev.png)

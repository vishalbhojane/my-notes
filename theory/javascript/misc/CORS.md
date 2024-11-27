Cross origin resource sharing
CORS is mechanism which uses additional http headers, to tell the browser, whether a specific web app can share resource with another web app
note: both web apps should have different origins e.g. a.com and b.com

### Before CORS

`https://vishal.com` cannot access resources from
`google.com/api/getData`
`api.vishal.com`
`vishal.com:5050`
`http://vishal.com`

---
### Steps

When domain A request resources from B, generally CORS pre-flight mechanism is followed
a pre-flight options call is made before the actual API call is made
server / domain B will check the options and verify it
after verification server / domain B will send the addition headers
`Accept-Control-Allow-Origin: * `
any domain is allowed to call 

`Accept-Control-Allow-Origin: https://vishal.com`
only `https://vishal.com` can access 

Methods
`Accept-Control-Allow-Methods`
`Post`, `Put`, `Delete`, `Get`

Once browsers knows that it is safe, it will make a actual call

---
### Types of access control mechanism
1. simple request
2. pre-flight request

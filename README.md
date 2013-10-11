# Http Auth Module
This is Simple Http Authentication HttpModule for ASP.NET (MVC).
- Basic Authentication
- Digest Authentication 
- Restrict IP Address (ip4 or ip6)
- Basic or Digest Authentication don't tounch HttpContext.Current.User.

# Quick start
Get Nuget package.
https://www.nuget.org/packages/HttpAuthModule/

```
PM> Install-Package HttpAuthModule
``` 

After Getting, configure Web.config file.
It's all you do for using HttpAuthModule.

# Configuration
modify Web.config file.

```XML
<appSettings>
	<!-- HttpAuth -->
	<!--
	  Http Authentication Mode.
	  - Basic: Basic authentication
	  - Digest: Digest authentication
	  - None: No authentication -->
	<add key="HttpAuth" value="Digest" />
	<add key="HttpAuth.Realm" value="SecureZone" />
	<!-- user1:pass1;user2:pass2;... -->
	<add key="HttpAuth.Credentials" value="hoge:hogepass;foo:foopass;"/>
	<!-- Digest Auth Nonce Valid Duration.(Minutes) -->
	<add key="HttpAuth.DigestNonceValidDuration" value="120" />
	<!--
	  When HttpAuth.RestrictIPAddresses is set, specified IPs are only allowed: otherwize All IPs are allowed.
	  value is joined IP Range Combination as following.
	  - 10.23.0.0/24
	  - 127.0.0.1 (equals to 127.0.0.1/32)
	  - 2001:0db8:bd05:01d2:288a:1fc0:0001:0000/16
	  - ::1 (equals to ::1/128)
	  
	  e.g) 127.0.0.1;182.249.0.0/16;182.248.112.128/26;::1
	-->
	<add key="HttpAuth.RestrictIPAddresses" value="127.0.0.1;::1" />
</appSettings>
<system.webServer>
    <modules>
      <add type="HttpAuthModule.HttpAuthModule" name="HttpAuthModule"/>
    </modules>
  </system.webServer>
```


### Context User

Get the current User

```cs
Sitecore.Security.Accounts.User contextUser = Sitecore.Context.User;
```

See if a user is logged in

```cs
if (Sitecore.Context.IsLoggedIn) {
//TODO: handle case that user is authenticated }
else {
//TODO: handle case that user is not authenticated }
```
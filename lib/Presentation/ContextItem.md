### Context Item

Get current Item

```cs
Sitecore.Data.Items.Item contextItem = Sitecore.Context.Item;
```

Get current Sitecore

```cs
Sitecore.Sites.SiteContext contextSite = Sitecore.Context.Site;
```

Get home Item

```cs
Sitecore.Sites.SiteContext contextSite = Sitecore.Context.Site;
Sitecore.Data.Items.Item home = Sitecore.Context.Database.GetItem(contextSite.StartPath);
```

Get current Database

```cs
Sitecore.Data.Database contextDatabase = Sitecore.Context.Database;
```

Get current language

```cs
Sitecore.Globalization.Language contextLanguage = Sitecore.Context.Language;
```

Get current device

```cs
Sitecore.Data.Items.DeviceItem contextDevice = Sitecore.Context.Device;
```

Get Raw URL

```cs
string rawUrl = Sitecore.Context.RawUrl;
```

Get Page Mode

```cs
if (Sitecore.Context.PageMode.IsPageEditor) {
}
```

Get URL of current Item

```cs
 Sitecore.Data.Items.Item contextItem = Sitecore.Context.Item; 
 string url = Sitecore.Links.LinkManager.GetItemUrl(contextItem);
 ```
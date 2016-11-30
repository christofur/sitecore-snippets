### Set Context Device Pipeline

Set the Context Device based on the User Agent string we find in the request object:

```cs
namespace Sitecore.Sharedsource.Pipelines.HttpRequest {
    public class FeedDeviceResolver {

        public void Process(Sitecore.Pipelines.HttpRequest.HttpRequestArgs args) {
            
            System.Web.HttpContext httpContext = System.Web.HttpContext.Current;
            
            if (httpContext == null || httpContext.Request == null || httpContext.Request.UserAgent == null || Sitecore.Context.Database == null)
            {
                return;
            }


            string agent = httpContext.Request.UserAgent;

            if (agent.Contains("feedfetcher")
            || agent.Contains("newsgatoronline")
            || agent.Contains("bloglines")
            || agent.Contains("yahoofeedseeker")) {
  
                Sitecore.Data.Items.DeviceItem device = Sitecore.Context.Database.Resources.Devices["Feed"];
  
                if (device != null)
                {
                    Sitecore.Context.Device = device; 
                }
           }
        }
    }
}
```

Activate the pipeline:

```xml
<httpRequestBegin>
...
    <processor type="Sitecore.Sharedsource.Pipelines.HttpRequest.FeedDeviceResolver, Assembly" />
    <processor type="Sitecore.Pipelines.HttpRequest.DeviceResolver, Sitecore.Kernel" /> 
...
```
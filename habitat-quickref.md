# Habitat Reference Sheet

## Razor

### Forms & Validation
`
@Html.ValidationMessage("invalidCredentials", new { @class = "alert alert-danger" }, "div")
@Html.LabelFor(x => x.Email, new { @class = "control-label"})
@Html.TextBoxFor(x => x.Email, new { @class = "form-control", id = "popupLoginEmail", @placeholder = Html.Sitecore().Dictionary("/Accounts/Login/Login E-mail Placeholder", "Enter your e-mail")})
@Html.ValidationMessageFor(x => x.Email, "", new { @class = "help-block" }, "p")
@Html.ValidationErrorFor(x=>x.Password, "has-error")
@Html.PasswordFor(x => x.Password, new { @class = "form-control", id = "popupLoginPassword", @placeholder = Html.Sitecore().Dictionary("/Accounts/Login/Login Password Placeholder", "Enter your password") })
@using (Html.BeginForm("Logout", "Accounts", FormMethod.Post))
@using (Html.BeginRouteForm(MvcSettings.SitecoreRouteName, FormMethod.Post, new..
@Html.Hidden("ReturnUrl", Model.ReturnUrl)
@Html.AddUniqueFormId()
@Html.ValidationSummary(true)
`
### Security
`
@if (!(Sitecore.Context.IsLoggedIn && Sitecore.Context.PageMode.IsNormal))
`
### Content Gets
`
@Html.Sitecore().DictionaryField("/Accounts/Login/Login", "Login")
@Html.Sitecore().ImageField(Templates.Identity.Fields.Logo, identity, mh: 50)
@Model.Rendering.Parameters.ToJson()
@element.Item.ImageUrl(Templates.HasMediaImage.Fields.Image, new MediaUrlOptions(maxWidth, 0, false))
@Html.Sitecore().ImageField(thumbnailField, Model.Item, mw: ThumbnailWidth, cssClass: "img-responsive")
@Html.Sitecore().CurrentRendering.Item.Url()
`
### Checks and Errors
`
@if (item.FieldHasValue(summaryField)
@if (!Model?.Item?.IsDerived(Templates.HasMediaSelector.ID) ?? true) { @Html.PageEditorError(AlertTexts.InvalidDataSourceTemplate(Templates.HasMediaSelector.ID), AlertTexts.InvalidDataSourceTemplateFriendlyMessage, Model.Item?.ID, Model.Rendering.Item?.ID) return;}
@if (element.Item.IsDerived(Templates.HasMediaVideo.ID)) { <span class="fa fa-play-circle icon-lg"></span> }
@Html.PageEditorError(AlertTexts.InvalidDataSourceTemplate(Templates.NewsArticle.ID), AlertTexts.InvalidDataSourceTemplateFriendlyMessage, Model.Item?.ID, Model.Rendering.Item?.ID)
`
### Layout 
`
@Html.Partial("~/Views/Accounts/_Login.cshtml", new LoginInfo())
@Html.Sitecore().DynamicPlaceholder("col-narrow-1", Model.Rendering.GetUseStaticPlaceholderNames())
@Html.Sitecore().Placeholder("postfooter")
@Html.RenderStyles(styles.Select(s => Constants.ScriptsBaseUrl + s).ToArray())
@Html.RenderScripts(scripts.Select(s => Constants.ScriptsBaseUrl + s).ToArray())
`
### General conventions

1. Create lots of HTML Helpers instead of logic in pages!
2. Instead of IFs in page, designate to a GetLink() helper method which contains the logic and is testable!
3. If there are any visual toggles you want to add to a component, use Rendering Parameters

## Controllers


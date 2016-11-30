### Binding Data

Create a Presentation Component

```html
<asp:dropdownlist runat="server" id="lstDropDown" />
```

Bind items to this Drop Down List

```cs
Sitecore.Data.Items.Item contextItem = Sitecore.Context.Item; 
lstDropDown.DataSource = contextItem.Children; 
lstDropDown.DataTextField = "name"; 
lstDropDown.DataValueField = "id";
lstDropDown.DataBind();
```

Populate a drop-down with page titles (for a navigation control)

```cs
Sitecore.Data.Items.Item contextItem = Sitecore.Context.Item;
foreach (Sitecore.Data.Items.Item child in contextItem.Children) {
    System.Web.UI.WebControls.ListItem option = new System.Web.UI.WebControls.ListItem(child.Name, child.ID.ToString());
    lstDropDown.Items.Add(option); 
}
```


Create an ASP.NET repeater with Sitecore children items

```html
<table border="1">
         <tr>
           <th>Item</th>
           <th>Title</th>
         </tr>
        <asp:Repeater ID="repeater" runat="server"> 
        <ItemTemplate>
            <tr> 
                <td>
                    <asp:Label runat="server" ID="Name" Text='<%#DataBinder.Eval(Container.DataItem,"Name")%>'></asp:Label>
                </td> 
                <td>
                    <asp:Label runat="server" ID="Title" Text='<%#DataBinder.Eval(Container.DataItem,@"[""title""]")%>'></asp:Label> 
                </td>
            </tr>
        </ItemTemplate>
        </asp:Repeater>
</table>
```

And populate with:

```cs
repeater.DataSource = Sitecore.Context.Item.Children;
repeater.DataBind();
```
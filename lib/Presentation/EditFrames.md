### Edit Frames

Wrap some markup in an `EditFrame` to create a new clickable region in Experience Editor mode. 

The buttons that appear in the context menu are those listed in the `core` database under `/core/sitecore/content/Applications/WebEdit/Edit Frame Buttons/Pet Details` 

```html
<sc:EditFrame ID="EditFrame1" Buttons="Pet Details" runat="server">
    <p>Phone us for more details about this animal.</p>
</sc:EditFrame>
```
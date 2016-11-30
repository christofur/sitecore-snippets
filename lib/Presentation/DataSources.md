### Data Sources

Find a DataSource and use this source to populate a number of presentation components:

```cs
var datasource = Attributes["sc_datasource"];

if (!string.IsNullOrEmpty(datasource))
{
    MainHeading.DataSource =
    MainImage.DataSource =
    MainText.DataSource =
    datasource;
}

```
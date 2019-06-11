# v8UmbracoNews

[https://our.umbraco.com/documentation/Umbraco8FAQ#will-it-be-possible-to-upgrade-automatically-from-umbraco-7-to-umbraco-8](https://our.umbraco.com/documentation/Umbraco8FAQ#will-it-be-possible-to-upgrade-automatically-from-umbraco-7-to-umbraco-8)

[https://our.umbraco.com/forum/umbraco-8/96923-v7-to-v8-data-migration#comment-306520](https://our.umbraco.com/forum/umbraco-8/96923-v7-to-v8-data-migration#comment-306520)

[https://github.com/KevinJump/uSync8/issues/14#issuecomment-487598751](https://github.com/KevinJump/uSync8/issues/14#issuecomment-487598751)

## example usync backup DocumentType

```diff
<?xml version="1.0" encoding="utf-8"?>
--<DocumentType>
++<ContentType Key="ca1a8bab-4434-42a2-a512-65a362e86bb0" Alias="header" Level="2">
    <Info>
--    <Key>ca1a8bab-4434-42a2-a512-65a362e86bb0</Key>
      <Name>Header</Name>
--    <Alias>header</Alias>
      <Icon>icon-document</Icon>
      <Thumbnail>folder.png</Thumbnail>
      <Description>Header-Items</Description>
      <AllowAtRoot>False</AllowAtRoot>
      <IsListView>False</IsListView>
      <Folder>Compositions</Folder>
      <Compositions />
      <DefaultTemplate></DefaultTemplate>
      <AllowedTemplates />
    </Info>
    <Structure />
    <GenericProperties>
      <GenericProperty>
        <Key>66d3c6f6-02ba-405f-9e6d-9d0b67520c71</Key>
        <Name>HeaderLinks</Name>
        <Alias>headerLinks</Alias>
        <Definition>b4e3535a-1753-47e2-8568-602cf8cfee6f</Definition>
        <Type>Umbraco.RelatedLinks2</Type>
        <Mandatory>false</Mandatory>
        <Validation></Validation>
        <Description><![CDATA[Links im Headerbereich neben Menü, z.B. Kontakt]]></Description>
        <SortOrder>0</SortOrder>
        <Tab>Header</Tab>
      </GenericProperty>
    </GenericProperties>
    <Tabs>
      <Tab>
        <Caption>Header</Caption>
        <SortOrder>3</SortOrder>
      </Tab>
    </Tabs>
--</DocumentType>
++</ContentType>
```

## custom grid components

[https://our.umbraco.com/apidocs/v8/ui/#/api/umbraco.services.editorService](https://our.umbraco.com/apidocs/v8/ui/#/api/umbraco.services.editorService)

dialogService -> editorService

### usage umbraco property editors

<ng-form name="form"> is required

```diff
--<umb-editor model="RTEcontent"></umb-editor>
++<umb-property-editor model="RTEcontent"></umb-property-editor>
```

## views

```diff
--@Model.Content.Text
++@Model.Text
```

```diff
--var isImage = stage.StageImage.DocumentTypeAlias == "Image";
++var isImage = stage.StageImage.IsDocumentType("Image");
```

```diff
--@Umbraco.If(singleColumn, "</div>")
++@Html.If(singleColumn, "</div>")
```

```diff
--var urlProvider = UmbracoContext.Current.UrlProvider;
++var urlProvider = Umbraco.Web.Composing.Current.UmbracoContext.UrlProvider;
```

### related links

The related links on Umbraco 8 changed to Multi Url Picker

[https://our.umbraco.com/forum/umbraco-8/96405-related-links-umbraco-8#comment-304799](https://our.umbraco.com/forum/umbraco-8/96405-related-links-umbraco-8#comment-304799)

## models

```diff
--public class EmailOptInPage : RenderModel
++public class EmailOptInPage : ContentModel
```

# Data.Paging.X.PagedList.AspNetCore.Mvc

Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc

Inspiration repository https://github.com/hieudole/PagedList.Core.Mvc

Reason asimilation repository are dependent on https://github.com/troygoode/PagedList is obsolete .

## Installation

1. Install-Package Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc

2. Edit `_ViewImports.cshtml`

```diff
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers
+ @addTagHelper *, Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc
```

## Usage
```html
<pager class="pager-container" list="@Model.SearchResult.SearchHits" options="@PagedListRenderOptions.Bootstrap4" asp-action="Index" asp-controller="Search" asp-route-query="@Model.SearchResult.SearchQuery" />
```
## Sample

![Sample](./assets/SearchResult.jpg?raw=true)


![Olbrasoft Paging Icon](https://raw.githubusercontent.com/Olbrasoft/Data.Paging.X.PagedList.AspNetCore.Mvc/master/olbrasoft-x-paged-list.png)
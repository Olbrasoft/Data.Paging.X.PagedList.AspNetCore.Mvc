# Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc

[![Build & Publish](https://github.com/Olbrasoft/Data.Paging.X.PagedList.AspNetCore.Mvc/actions/workflows/publish-nuget.yml/badge.svg)](https://github.com/Olbrasoft/Data.Paging.X.PagedList.AspNetCore.Mvc/actions/workflows/publish-nuget.yml)
[![NuGet](https://img.shields.io/nuget/v/Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc.svg)](https://www.nuget.org/packages/Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc/)
[![NuGet Downloads](https://img.shields.io/nuget/dt/Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc.svg)](https://www.nuget.org/packages/Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![.NET](https://img.shields.io/badge/.NET-8.0%20%7C%209.0%20%7C%2010.0-blue)](https://dotnet.microsoft.com/)

A TagHelper for ASP.NET Core MVC providing Bootstrap 4 compatible pagination using [X.PagedList](https://github.com/dncuug/X.PagedList).

## Features

- **Pager TagHelper** - Easy-to-use pagination component for Razor views
- **Bootstrap 4 Support** - Built-in Bootstrap 4 styling options
- **Customizable** - Configurable render options for pagination appearance
- **Route Integration** - Seamless integration with ASP.NET Core routing
- **Multi-framework Support** - Targets .NET 8.0, 9.0, and 10.0

## Installation

```bash
dotnet add package Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc
```

Or via Package Manager:

```powershell
Install-Package Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc
```

## Quick Start

### 1. Configure TagHelper

Edit `_ViewImports.cshtml`:

```diff
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers
+ @addTagHelper *, Olbrasoft.Data.Paging.X.PagedList.AspNetCore.Mvc
```

### 2. Use in Views

```html
<pager
    class="pager-container"
    list="@Model.SearchResult.SearchHits"
    options="@PagedListRenderOptions.Bootstrap4"
    asp-action="Index"
    asp-controller="Search"
    asp-route-query="@Model.SearchResult.SearchQuery" />
```

### 3. Complete Example

**Controller:**

```csharp
public class SearchController : Controller
{
    public async Task<IActionResult> Index(string query, int page = 1)
    {
        var pageSize = 10;
        var results = await _searchService.SearchAsync(query);
        var pagedResults = results.ToPagedList(page, pageSize);

        return View(new SearchViewModel
        {
            SearchQuery = query,
            SearchHits = pagedResults
        });
    }
}
```

**View:**

```html
@model SearchViewModel

<div class="search-results">
    @foreach (var hit in Model.SearchHits)
    {
        <div class="result-item">
            <h3>@hit.Title</h3>
            <p>@hit.Description</p>
        </div>
    }
</div>

<nav aria-label="Search results pages">
    <pager
        class="pagination justify-content-center"
        list="@Model.SearchHits"
        options="@PagedListRenderOptions.Bootstrap4"
        asp-action="Index"
        asp-controller="Search"
        asp-route-query="@Model.SearchQuery" />
</nav>
```

## Pager Attributes

| Attribute | Description |
|-----------|-------------|
| `list` | The `IPagedList` instance to paginate |
| `options` | Render options (e.g., `PagedListRenderOptions.Bootstrap4`) |
| `asp-action` | The action method for pagination links |
| `asp-controller` | The controller for pagination links |
| `asp-route-*` | Additional route parameters |
| `class` | CSS classes for the pager container |

## Sample Output

![Sample pagination](./assets/SearchResult.jpg?raw=true)

## Dependencies

- [X.PagedList.Mvc.Core](https://www.nuget.org/packages/X.PagedList.Mvc.Core/) - PagedList MVC integration

## Inspiration

This package was inspired by [PagedList.Core.Mvc](https://github.com/hieudole/PagedList.Core.Mvc). It was created because the original [PagedList](https://github.com/troygoode/PagedList) repository is now obsolete and has been replaced by X.PagedList.

## Multi-Targeting Support

| Target Framework | Status |
|------------------|--------|
| .NET 8.0 | Supported |
| .NET 9.0 | Supported |
| .NET 10.0 | Supported |

## Building from Source

```bash
git clone https://github.com/Olbrasoft/Data.Paging.X.PagedList.AspNetCore.Mvc.git
cd Data.Paging.X.PagedList.AspNetCore.Mvc
dotnet restore
dotnet build
```

## License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## Authors

- **Jiří Tůma**
- **Brian Le**
- **Company**: Olbrasoft
- **Repository**: [https://github.com/Olbrasoft/Data.Paging.X.PagedList.AspNetCore.Mvc](https://github.com/Olbrasoft/Data.Paging.X.PagedList.AspNetCore.Mvc)

---

![Olbrasoft Paging Icon](./olbrasoft-x-paged-list.png)

**Copyright © 2020-2025 Olbrasoft**

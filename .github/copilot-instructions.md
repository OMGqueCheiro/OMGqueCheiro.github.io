# Copilot Instructions for OMGqueCheiro.github.io

## Project Overview
- This is a Blazor WebAssembly project targeting .NET 9, designed for static deployment to GitHub Pages.
- The architecture is component-based, with reusable UI elements in `Components/`, page-level views in `Pages/`, and layout/navigation in `Layout/`.
- Data models are defined in `Model/` (e.g., `ProductModel`, `TestimonialModel`).
- Static assets (CSS, images, manifest, service worker) are in `wwwroot/`.

## Build & Deployment
- **Local build:** Use `dotnet build` and `dotnet run` for development.
- **Production publish:** `dotnet publish OMGqueCheiro.csproj -c:Release -o docs --nologo` outputs to `docs/` for GitHub Pages.
- **GitHub Actions:** `.github/workflows/main.yml` automates build and deploy on push to `main`.
- **WASM tools:** Ensure `dotnet workload install wasm-tools` before publishing.

## Key Patterns & Conventions
- **Component usage:** UI is composed from `.razor` files in `Components/` and `Pages/`. Layouts are set in `App.razor` and `MainLayout.razor`.
- **Routing:** Pages in `Pages/` are routed automatically. Nested pages (e.g., `Pages/Produtos/`) represent product categories.
- **Styling:** Use `.razor.css` for component-scoped styles and `wwwroot/css/app.css` for global styles.
- **MudBlazor:** UI components leverage MudBlazor (`builder.Services.AddMudServices()` in `Program.cs`).
- **Data:** Static sample data (e.g., `weather.json`) is in `wwwroot/sample-data/`.
- **Service worker:** Configured for PWA via `service-worker.js` and manifest.

## External Dependencies
- **NuGet:** Main dependencies are `Microsoft.AspNetCore.Components.WebAssembly` and `MudBlazor` (see `OMGqueCheiro.csproj`).
- **Bootstrap:** Included in `wwwroot/lib/bootstrap/` for additional styling.

## Development Tips
- **Add new pages/components:** Place in `Pages/` or `Components/` and update navigation in `NavMenu.razor` if needed.
- **Debugging:** Use browser dev tools and Blazor error output. For build issues, check `.github/workflows/main.yml` for CI steps.
- **Testing:** No explicit test project found; add tests in a `Tests/` folder if needed.

## Example Workflow
1. Add a new product category: create a `.razor` file in `Pages/Produtos/`.
2. Update navigation in `NavMenu.razor`.
3. Build locally with `dotnet build`.
4. Commit and push to `main` for auto-deploy.

---
_If any section is unclear or missing, please provide feedback to improve these instructions._

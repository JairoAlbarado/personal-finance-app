
# Approved Stack

This document defines the approved, trial, and forbidden technology stack by category. New stack decisions must be planned before being added to this document.

## WEB FRAMEWORKS

### Trial

| name | version | ADR link | description |
|---|---|---|---|

### Approved

| name | version | ADR link | description |
|---|---|---|---|
| Astro | 7.4 | [Documentation App ADR](docs/adr/desing-system/documentation-app.md) | Static site generator for the design system documentation. |

### Forbidden

| name | version | ADR link | description |
|---|---|---|---|

## PACKAGE MANAGERS

### Trial

| name | version | ADR link | description |
|---|---|---|---|

### Approved

| name | version | ADR link | description |
|---|---|---|---|
| pnpm Workspaces | Not specified | [Package Manager ADR](docs/adr/tech-stack/package-manager.md) | Manages monorepo workspaces and local package dependencies using the `workspace:*` protocol. |

### Forbidden

| name | version | ADR link | description |
|---|---|---|---|

## REPOSITORY STRUCTURE VALIDATION

### Trial

| name | version | ADR link | description |
|---|---|---|---|

### Approved

| name | version | ADR link | description |
|---|---|---|---|
| ls-lint | Not specified | [Folder Structure Manifest ADR](docs/adr/tech-stack/folder-structure-manifest.md) | Validates repository folder and file naming conventions. |

### Forbidden

| name | version | ADR link | description |
|---|---|---|---|


### Forbidden
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `eslint-plugin-project-structure for filesystem layout validation` | `N/A` | [`folder-structure-manifest.md`](docs/adr/tech-stack/folder-structure-manifest.md) | Considerado pero no seleccionado para la validación de la estructura del sistema de archivos; se usa `ls-lint` para ese rol. Esto no prohíbe ESLint para tareas de *linter* no relacionadas. |

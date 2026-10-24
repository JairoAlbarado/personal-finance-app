# Approved Stack

Este documento lista las tecnologías aprobadas, en prueba y prohibidas del proyecto por categoría. Los colaboradores y agentes de IA deben seguir el estado aquí registrado y consultar los Registros de Decisiones de Arquitectura (ADR) vinculados para obtener contexto.

Las nuevas decisiones sobre el *stack*, elecciones de versiones y reemplazos deben planificarse y justificarse en un ADR antes de su implementación. No infieras la aprobación a partir de una propuesta ni selecciones una versión exacta que no haya sido decidida y documentada.

## Definiciones de Estado

* **Trial (En prueba):** Propuesto o bajo evaluación; aún no aprobado como parte del *stack* del proyecto.
* **Approved (Aprobado):** Seleccionado para el rol específico indicado en la fila. La aprobación no significa que se deba instalar obligatoriamente cada integración opcional.
* **Forbidden (Prohibido):** No debe usarse para el rol específico indicado en la fila. Esto no constituye automáticamente una prohibición general en todo el repositorio para usar la tecnología con otro propósito.
* Un enlace ADR faltante significa que no se encontró un ADR de respaldo entre los tres ADR revisados para este manifiesto.

---

## Package Manager and Workspaces

### Trial
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| No entries | —— | —— | Ninguna tecnología de gestor de paquetes está designada como en prueba por los ADR revisados. |

### Approved
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `pnpm Workspaces` | No especificado por este ADR | [`package-manager.md`](docs/adr/tech-stack/package-manager.md) | Usa `pnpm Workspaces` y `workspace:*` para paquetes locales. Los paquetes internos pueden exponer puntos de entrada de código fuente sin un paso de compilación intermediario. Cada paquete debe declarar sus propias dependencias. Este ADR aprueba la estrategia de espacios de trabajo, no una versión específica del CLI de pnpm. |
| `pnpm CLI` | `12.x` (versión exacta pendiente) | ADR pendiente; [`package-manager.md`](docs/adr/tech-stack/package-manager.md) cubre solo la estrategia de espacios de trabajo | El mantenedor ha indicado que se usará `pnpm 12`. El ADR revisado no justifica ni fija esta versión del CLI. Un ADR dedicado debe registrar la justificación, seleccionar la versión exacta y definir cómo se aplicará la versión antes de que la implementación dependa de una versión específica. |

### Forbidden
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `npm Workspaces` | `N/A` | [`package-manager.md`](docs/adr/tech-stack/package-manager.md) | Considerado pero no seleccionado como el gestor de espacios de trabajo del monorepo. No lo sustituyas por `pnpm Workspaces` sin un ADR que lo suprima. Esto no prohíbe `npm` para fines no relacionados. |
| `Yarn Workspaces` | `N/A` | [`package-manager.md`](docs/adr/tech-stack/package-manager.md) | Considerado pero no seleccionado como el gestor de espacios de trabajo del monorepo. No lo sustituyas por `pnpm Workspaces` sin un ADR que lo suprima. Esto no prohíbe `Yarn` para fines no relacionados. |

---

## Documentation Application and Build Tooling

### Trial
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| No entries | —— | —— | Ningún generador de documentación está designado como en prueba por los ADR revisados. |

### Approved
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `Astro` | `7.4` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Seleccionado como el generador de sitios estáticos para `apps/docs`; el ADR especifica salida estática y cero tiempo de ejecución de framework del lado del cliente por defecto. |
| `Vite` | `8` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Especificado como parte de la configuración seleccionada de `Astro 7.4` para la resolución de CSS en espacios de trabajo y HMR. El ADR no fija una versión de parche exacta. |

### Forbidden
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `Eleventy (11ty)` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Considerado pero no seleccionado como la aplicación/compilador de documentación. No lo sustituyas por `Astro` en este rol sin un nuevo ADR. |
| `Zola` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Considerado pero no seleccionado como la aplicación/compilador de documentación. No lo sustituyas por `Astro` en este rol sin un nuevo ADR. |
| `Storybook HTML (@storybook/html-vite)` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Considerado pero no seleccionado como la aplicación/compilador/entorno de documentación en este ADR. Esto no es una prohibición general de Storybook para futuros usos no relacionados. |

---

## Styling Architecture

### Trial
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| No entries | —— | —— | Ninguna tecnología de estilos está designada como en prueba por los ADR revisados. |

### Approved
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `Decoupled standalone CSS ruleset` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Mantiene el paquete de estilos del sistema de diseño (`packages/design-system`) independiente de la aplicación de documentación (`apps/docs`). |
| `Tailwind CSS` | `v4` (versión exacta no especificada) | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | El ADR describe el conjunto de reglas CSS independientes compiladas mediante `Tailwind CSS v4`. |
| `Native CSS Cascade Layers (@layer)` | `N/A` (función nativa de CSS) | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Usa capas de cascada CSS para estructurar la hoja de estilos del sistema de diseño y preservar el orden de cascada deseado. |
| `Inverted Triangle CSS (ITCSS)` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Usa `ITCSS` como la metodología de organización de la hoja de estilos. |

### Forbidden
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `Unplanned replacement of the approved CSS architecture` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | No reemplaces el enfoque de CSS desacoplado, Cascade Layers, ITCSS o Tailwind CSS v4 para el sistema de diseño sin un nuevo ADR. |
| `Styling transformations that mutate design-system selectors or cascade-layer order` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | La compilación de la documentación no debe inyectar *hashes* de selectores con ámbito en los selectores del sistema de diseño ni alterar el orden de cascada nativo `@layer`. |

---

## Documentation Content and Metadata

### Trial
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| No entries | —— | —— | Ninguna tecnología de contenido o metadatos está designada como en prueba por los ADR revisados. |

### Approved
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `@astrojs/mdx` | No especificado | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Usa la integración MDX de Astro para contenido `.mdx`, incluyendo expresiones JSX y transformaciones AST de Markdown/MDX en tiempo de compilación. |
| `remark / rehype AST pipeline` | Plugins específicos no especificados | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | El ADR requiere soporte para transformaciones AST personalizadas de `remark/rehype`; los plugins individuales deben elegirse solo cuando sea necesario. |
| `Zod` | No especificado | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Valida el *frontmatter* y los metadatos de contenido de la documentación en tiempo de compilación. |
| `Astro framework integrations (@astrojs/react, @astrojs/vue, @astrojs/svelte, @astrojs/solid-js)` | No especificado; opcional | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Soportado para ejemplos aislados cuando sea necesario. Son opcionales, no un requisito para instalar todas las integraciones o habilitar la hidratación por defecto. |

### Forbidden
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `Default Markdown/MDX syntax highlighting that wraps code tokens in <span> elements` | Deshabilitado por decisión | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Configura `markdown: { syntaxHighlight: false }` para que `<pre><code>` pueda preservar la estructura de nodo de texto requerida por la API CSS Custom Highlight planeada. |
| `Unapproved default client-side hydration on core CSS documentation pages` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | La documentación debe renderizar HTML estático por defecto. Agrega hidratación `client:*` a las páginas principales solo cuando exista una excepción explícita y documentada. |
| `Reverse dependency from packages/design-system to documentation/framework tooling` | `N/A` | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | El límite de dependencia es unidireccional: `apps/docs` puede importar puntos de entrada de CSS desde `packages/design-system`, pero el paquete del sistema de diseño no debe depender de Astro, MDX o paquetes de frameworks de UI. |

---

## Repository Structure and Dependency Validation

### Trial
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| No entries | —— | —— | Ninguna tecnología de validación de repositorios está designada como en prueba por los ADR revisados. |

### Approved
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `ls-lint (@ls-lint/ls-lint)` | No especificado | [`folder-structure-manifest.md`](docs/adr/tech-stack/folder-structure-manifest.md) | Usa un archivo raíz `.ls-lint.yml` para validar la estructura de directorios, convenciones de nomenclatura, archivos requeridos y directorios raíz permitidos. El ADR exige una comprobación obligatoria en CI y un *hook* de `git pre-commit`. |
| `dependency-cruiser` | No especificado | [`documentation-app.md`](docs/adr/desing-system/documentation-app.md) | Usa la verificación de límites de espacio de trabajo para hacer cumplir dependencias unidireccionales desde `apps/docs` hacia los puntos de entrada de CSS en `packages/design-system`, y no al revés. |

### Forbidden
| Nombre | Versión | Enlace ADR | Descripción |
| :--- | :--- | :--- | :--- |
| `eslint-plugin-project-structure for filesystem layout validation` | `N/A` | [`folder-structure-manifest.md`](docs/adr/tech-stack/folder-structure-manifest.md) | Considerado pero no seleccionado para la validación de la estructura del sistema de archivos; se usa `ls-lint` para ese rol. Esto no prohíbe ESLint para tareas de *linter* no relacionadas. |

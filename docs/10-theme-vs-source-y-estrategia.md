# Theme actual vs source FTP

## Objetivo

Definir como usar los SCSS descargados por FTP como fuente de contexto tecnico para modificar el theme sin depender de overrides fragiles en `theme.css`.

## Hallazgo principal

Los archivos del source FTP representan el theme base de Morelia:

- `Tienda Nube/css/style-critical.scss`: estructura critica, layout base, componentes, header, product grid y parte de product detail.
- `Tienda Nube/css/style-async.scss`: componentes no criticos, formularios, modales y utilidades visuales.
- `Tienda Nube/css/style-colors.scss`: color, tipografia, iconografia SVG y reglas dependientes de configuracion.

En cambio, `theme.css` funciona hoy como una capa editorial custom montada por encima del theme base. No parece ser el CSS compilado oficial del theme, sino una hoja de personalizacion final.

## Que implica esto

- El source FTP sirve para entender donde vive cada componente en el theme nativo.
- `theme.css` sirve para detectar que partes ya fueron intervenidas y con que nivel de agresividad.
- Si seguimos agregando reglas solo en `theme.css`, el riesgo de stacking de overrides va a crecer rapido.

## Zonas ya muy intervenidas en theme.css

### Header y nav

- Barra superior, header principal, logo, utilities, badge de carrito y nav desktop.
- Dropdown desktop con una capa visual fuerte y muchos `!important`.

### Product detail

- Scope principal correcto: `#single-product[data-store="product-detail"]`.
- Tipografia, precio, mensajes secundarios, variantes, cantidad, CTA y acordeon con personalizacion intensa.

### Quickshop

- Scope principal correcto: `#quickshop-modal`.
- Nombre, precio, variantes, cantidad, cierre, stock y CTA reescritos casi completos.

### Grillas y cards

- Unificacion amplia de cards para home, category, search y listados.
- Se reutiliza una misma direccion visual sobre `.item-*` y hooks `data-store="product-item-*"`.

## Zonas que todavia no muestran custom CSS

- `#related-products`
- `#complementary-products`

Esto es bueno: permite intervenir esos modulos con criterio limpio desde el principio, usando scopes estables y sin heredar deuda de overrides previos.

## Tipos de selector detectados

### Estables y recomendados

- `#single-product[data-store="product-detail"]`
- `#quickshop-modal`
- `[data-store="product-buy-button"]`
- `[data-component="product.add-to-cart"]`
- `[data-store^="product-item-name-"]`
- `[data-store^="product-item-price-"]`
- `[data-store="product-item-buy-button"]`
- `[data-store="product-item-buy-now"]`
- `[data-store="product-item-labels"]`
- `[data-store="home-image-text-module"]`

### Utiles pero de estabilidad media

- `.head-main`
- `.nav-desktop`
- `.desktop-list-subitems`
- `.item-name`
- `.item-description`
- `.item-actions`
- `.product-item-image-container`
- `.btn-variant`
- `.form-quantity-product`

### Fragiles o sensibles

- Casi cualquier selector con prefijo `js-` cuando existe una alternativa con `data-store`, id o clase visual.
- Selectores demasiado acoplados al markup puntual, por ejemplo `.row.no-gutters.align-items-center` o cadenas largas de utilitarias.
- Reglas que dependen de `*` dentro de CTAs para forzar color o uppercase.

## Regla de trabajo recomendada

### Cuando modificar el theme base

Conviene pensar el cambio como parte del theme base cuando:

- afecta un componente estructural de Morelia;
- reemplaza estilos repetidos en varias pantallas;
- hoy requiere demasiado `!important` para imponerse;
- depende de layout, spacing o comportamiento visual nativo del componente.

En esos casos, el source FTP nos indica donde vive la pieza original:

- header, wrappers, grilla y varios componentes base: `style-critical.scss`
- modales, formularios y transiciones: `style-async.scss`
- color, tipografia y SVG: `style-colors.scss`

### Cuando dejarlo como CSS custom final

Conviene dejarlo como capa final si:

- es una decision editorial local y acotada;
- aplica a una sola seccion puntual;
- no justifica recompilar o tocar varias piezas del theme;
- necesita convivir con limitaciones del editor o del admin preview.

## Estrategia para evitar overrides nuevos

1. Antes de tocar una seccion, ubicar primero el scope estable del modulo.
2. Revisar si el cambio corresponde al componente base en los SCSS FTP o a una capa editorial puntual.
3. Si el cambio es estructural, editar mentalmente el origen correcto del theme y usar `theme.css` solo como traduccion minima temporal.
4. Si el cambio es local, scopearlo por modulo y no por utilitarias sueltas.
5. Evitar agregar nuevas reglas globales sobre `.js-*` si existe un anchor mejor.
6. Evitar cadenas largas de selectores repetidos entre home, category, search y listados cuando se pueda trabajar sobre un scope comun validado.
7. Reducir `!important` solo cuando el selector ya nace con suficiente especificidad y el componente no lo necesita para sobrevivir al cascade del theme.

## Decision operativa para este workspace

De ahora en adelante conviene usar los archivos FTP como referencia de origen del theme y `theme.css` como capa de customizaciones existentes.

Traduccion practica:

- Si vamos a tocar header, product detail, quickshop o cards, primero miramos el source FTP para entender la pieza base.
- Si vamos a tocar related o complementary, conviene arrancar directamente con scopes propios del modulo y sin copiar la logica pesada de overrides existente en otras areas.
- Si una regla nueva necesita demasiado `!important`, primero hay que revisar si estamos editando en la capa equivocada.

## Checklist previo a cualquier cambio nuevo

- Identificar modulo y scope estable.
- Confirmar si existe anchor `data-store` o id antes de usar `.js-*`.
- Decidir si el cambio es base theme o capa editorial.
- Reusar patrones ya validados en `02-mapa-selectores-theme-actual.md`.
- Evitar abrir una nueva familia de overrides si el problema nace en la estructura original del componente.
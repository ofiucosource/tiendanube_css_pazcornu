# Mapa de selectores del CSS actual

## Objetivo

Traducir los selectores usados hoy en `theme.css` a su significado funcional y a su nivel de respaldo documental.

## Leyenda de estabilidad

- Alta: selector o hook explicitamente respaldado por docs oficiales.
- Media: aparece alineado con patrones oficiales, pero puede variar entre themes o customizaciones.
- Baja: parece mas dependiente del marcado puntual del theme o de una capa visual no documentada.

## Navbar / Header

| Selector actual | Que parece representar | Respaldo documental | Estabilidad | Observacion |
| --- | --- | --- | --- | --- |
| `.head-info`, `.js-head-info`, `.js-informative-banner` | barra informativa superior | layout.tpl / header snipplets | Media | tipografia y espaciado seguros |
| `.head-main`, `.js-head-main` | header principal | layout.tpl / header snipplets | Media | borde y shadow seguros |
| `.logo-img-container` | wrapper del logo | header snipplets | Media | padding seguro |
| `.logo-img` | imagen del logo | header snipplets | Media | max-height y transicion seguros |
| `.utilities-container`, `.js-utilities-container` | iconos de buscar, usuario, carrito | header snipplets | Media | sensible a JS en su interior |
| `.js-cart-widget .js-cart-count`, `.head-cart .js-cart-count` | badge numerico del carrito | header snipplets | Media | no ocultar; tipografia segura |
| `.nav-desktop`, `.js-nav-desktop`, `.desktop-nav` | navegacion principal desktop | header snipplets | Media | tipografia y padding seguros |
| `.desktop-list-subitems` | dropdown de submenu desktop | theme Morelia | Media | componente visual del theme |
| `.item-with-subitems` | categoria padre con hijos en dropdown | theme Morelia | Baja | propio del theme |
| `.item-subitems-head` | encabezado de subcategoria en dropdown | theme Morelia | Baja | propio del theme |
| `.nav-category-name` | nombre de categoria en dropdown | theme Morelia | Baja | propio del theme |
| `.nav-list-link` | link general dentro del menu | theme Morelia | Media | patron visual del theme |
| `.js-search-input` | input del buscador | header snipplets | Media | tipografia y borde seguros |
| `.js-mobile-nav`, `.mobile-nav`, `.js-nav-mobile` | navegacion mobile (hamburger) | header snipplets | Media | tipografia segura |

## Detalle de producto

| Selector actual | Que parece representar | Respaldo documental | Estabilidad | Observacion |
| --- | --- | --- | --- | --- |
| `#single-product[data-store="product-detail"]` | contenedor padre del product detail | tutoriales de shipping y pagos | Alta | excelente scope principal |
| `.page-header` | encabezado del detalle | `page-header.tpl` | Alta | incluye breadcrumbs y h1 |
| `.page-header .breadcrumbs` | breadcrumbs de producto | `breadcrumbs.tpl` | Alta | seguro para tipografia y spacing |
| `.page-header h1` | titulo visible del producto | `page-header.tpl` | Alta | conviene mantener legibilidad y jerarquia |
| `[data-store^="product-name-"]` | hook oficial del nombre | `page-header.tpl` | Alta | mejor anchor que clases genericas |
| `.price-container` | wrapper de precio | `product-form.tpl` | Alta | zona sensible a cambio de variante |
| `#price_display` | precio principal | docs de pagos/cuotas | Alta | no ocultar sin validar CTA y variantes |
| `.js-price-display` | precio reactivo | docs de pagos/cuotas | Alta | JS actualiza este nodo |
| `.price-without-taxes-container` | texto secundario de precio/impuestos | patron oficial de storefront | Media | estilado seguro, ocultado con cuidado |
| `.js-product-payments-container` | cuotas / link a medios de pago | `installments.tpl` | Alta | no romper display/interaccion |
| `.js-product-discount-disclaimer` | mensaje de promo no combinable | articulo oficial | Alta | hook validado |
| `.js-discount-explanation` | explicacion secundaria de descuento | promociones / payments | Media | revisar visualmente si cambia wording |
| `.divider` | separador visual | docs de product-form, cart, page-header | Alta | seguro para espaciado y opacidad |
| `.js-free-shipping-message` | mensaje de envio gratis | `shipping-calculator.tpl` | Alta | texto dinamico |
| `.js-shipping-add-product-label` | aviso de shipping al sumar producto | shipping/cart flows | Media | sensible a flujo carrito |
| `.js-product-form-free-shipping-message` | mensaje de envio gratis en formulario | shipping/promo flows | Media | validar con producto elegible |
| `[data-variation-id] .form-label` | label de variante | `product-variants.tpl` / `form-select.tpl` | Media | muy util para texto, no para layout profundo |
| `.js-product-variants-group` | grupo de cada variante | `product-variants.tpl` | Alta | buen anchor estructural |
| `.btn-variant:not(.btn-variant-color)` | UI de variante tipo pill/texto | no visible en docs Base | Media | probablemente propio de Morelia/Rio family |
| `.btn-variant-color` | UI de variante color | no visible en docs Base | Media | no asumir misma estructura en todos los productos |
| `.js-added-to-cart-product-message` | mensaje de producto agregado | `product-form.tpl` | Alta | puede mostrarse/ocultarse por JS |
| `.js-product-stock` | mensaje de stock | labels/product flows | Media | revisar junto a variantes |
| `.js-shipping-minimum-label` | umbral de envio | shipping/promo flows | Media | contenido dinamico |
| `.js-free-shipping-discount-not-combinable` | mensaje promo/envio no combinable | promociones | Media | hook de negocio, no puramente visual |
| `.form-quantity-product` | wrapper visual de cantidad | cantidad/form patterns | Media | seguro para border, no para reorden fuerte |
| `.js-quantity-input` | input cantidad | `product-quantity.tpl` | Alta | sensible a usabilidad |
| `.js-quantity-down` / `.js-quantity-up` | controles cantidad | `product-quantity.tpl` | Alta | no desactivar pointer cues |
| `[data-store="product-buy-button"]` | boton de compra con hook oficial | storefront data-store | Alta | buen selector para CTA |
| `[data-component="product.add-to-cart"]` | componente add to cart | componente storefront | Alta | util como fallback moderno |
| `.js-addtocart-placeholder` | placeholder mientras procesa compra | `product-form.tpl` placeholders | Alta | no conviene eliminar |
| `.js-accordion-toggle` | toggle de acordeon | patron de UI del theme | Media | validar hover/focus |
| `.js-accordion-toggle .subtitle` | subtitulo del acordeon | patron del theme | Media | tipografia segura |
| `.product-description` | descripcion del producto | `product-form.tpl` | Alta | excelente anchor para tono editorial |
| `.font-small`, `.font-smallest` | clases utilitarias de tamaño de texto | Bootstrap / theme | Media | usadas en textos secundarios de precio y cuotas |
| `.opacity-60`, `.opacity-80` | clases utilitarias de opacidad | Bootstrap / theme | Media | usadas para atenuar mensajes secundarios |
| `.btn-variant:not(.btn-variant-color) .btn-variant-content` | contenido textual dentro de variante pill | theme Morelia | Media | hereda uppercase y color del padre |
| `.btn-variant-color .btn-variant-content` | swatch de color dentro de variante color | theme Morelia | Media | tamaño y display controlados |

## Quickshop modal

| Selector actual | Que parece representar | Respaldo documental | Estabilidad | Observacion |
| --- | --- | --- | --- | --- |
| `#quickshop-modal` | scope raiz del modal quickshop | theme Morelia | Alta | mejor anchor para overrides |
| `#quickshop-modal .quickshop-image-container` | wrapper de la imagen | theme Morelia | Media | fondo y overflow seguros |
| `#quickshop-modal .js-item-variants` | columna de info (nombre, precio, variantes, CTA) | theme Morelia | Media | scope principal de la mitad derecha |
| `#quickshop-modal #quickshop-form` | formulario de compra | theme Morelia | Media | scope directo del form |
| `#quickshop-modal .js-item-name` | nombre del producto | `grid/item.tpl` | Alta | tipografia segura |
| `#quickshop-modal .js-price-display` | precio reactivo | docs de pagos/cuotas | Alta | no ocultar |
| `#quickshop-modal .js-compare-price-display` | precio comparativo tachado | docs de pagos/cuotas | Media | visible solo con promo |
| `#quickshop-modal .form-label`, `.js-insta-variation-label` | label de variante | `product-variants.tpl` | Media | tipografia segura |
| `#quickshop-modal .js-product-variants-group` | grupo de cada variante | `product-variants.tpl` | Alta | buen anchor estructural |
| `#quickshop-modal .btn-variant:not(.btn-variant-color)` | variante tipo pill/texto | theme Morelia | Media | propio del theme |
| `#quickshop-modal .btn-variant-color` | variante tipo color swatch | theme Morelia | Media | propio del theme |
| `#quickshop-modal .form-quantity-product` | wrapper del stepper cantidad | theme Morelia | Media | border y layout seguros |
| `#quickshop-modal .js-quantity-input` | input de cantidad | `product-quantity.tpl` | Alta | sensible a usabilidad |
| `#quickshop-modal .js-quantity-down`, `.js-quantity-up` | controles de cantidad | `product-quantity.tpl` | Alta | no desactivar |
| `#quickshop-modal .js-prod-submit-form`, `.btn-add-to-cart` | boton de compra real | `product-form.tpl` | Alta | CTA principal |
| `#quickshop-modal .js-addtocart-placeholder` | placeholder de estados de compra | `product-form.tpl` | Alta | no eliminar |
| `#quickshop-modal .modal-close` | boton cerrar del modal | theme Morelia | Media | no ocultar |
| `#quickshop-modal .js-product-stock` | mensaje de stock | labels/product flows | Media | revisar junto a variantes |
| `#quickshop-modal #stock-notification-container` | modulo aviso de stock | custom / Morelia | Media | ids dedicados, facil de controlar |
| `svg.js-open-quickshop-icon.icon-inline` | icono de apertura quickshop en grid | theme Morelia | Baja | oculto intencionalmente en el CSS actual |

Nota: la estructura detallada del DOM de quickshop esta documentada en `06-quickshop-modal-contexto.md`. En este bloque el respaldo es mixto: snapshot operativo del DOM real + patrones oficiales de product, price y quantity.

## Home / grilla de productos

| Selector actual | Que parece representar | Respaldo documental | Estabilidad | Observacion |
| --- | --- | --- | --- | --- |
| `.section-featured-home` | bloque de destacados home | `home-featured-products.tpl` | Alta | scope principal correcto |
| `[data-store^="product-item-name-"]` | nombre de item con hook oficial | `grid/item.tpl` | Alta | preferible sobre wrappers |
| `.item-name` / `.js-item-name` | nombre del producto en card | `grid/item.tpl` | Alta | ambos aparecen en docs |
| `.item-description` | bloque textual de card | `grid/item.tpl` | Alta | seguro para spacing |
| `.item-price-container` | wrapper de precio | `grid/item.tpl` | Alta | conviene no alterar display inline/block sin revisar |
| `.item-price` | precio visible de item | `grid/item.tpl` | Alta | actualizado segun estado del producto |
| `[data-store^="product-item-price-"]` | precio con hook oficial | `grid/item.tpl` | Alta | anchor recomendado |
| `.item-image-container` | wrapper de imagen | patron de card | Media | overflow oculto es comun y seguro |
| `.item-image` | imagen del producto | `grid/item.tpl` | Alta | hover scale suave es seguro |
| `.item-link` | link contenedor de card | `grid/item.tpl` | Alta | conviene no bloquear click area |
| `.item-actions` | acciones de quickshop/compra | `grid/item.tpl` | Alta | puede variar segun quickshop |
| `.item-buy` | CTA o wrapper de compra | family patterns de cards | Media | depende del estado quickshop/direct add |
| `.item-description .btn` | botones dentro del texto del item | Bootstrap + theme | Media | util como fallback |
| `[data-store="product-item-buy-button"]` | boton compra de item | hook oficial storefront | Alta | excelente anchor |
| `[data-store="product-item-buy-now"]` | compra inmediata | hook oficial storefront | Alta | puede no existir segun configuracion |
| `.js-addtocart-placeholder-inline` | placeholder inline en cards | `grid/item.tpl` placeholder | Media | no aparece en tu CSS pero es vecino funcional |
| `.product-item-image-container` | wrapper alternativo de imagen en card | `grid/item.tpl` | Media | usado junto a `.item-image-container` |
| `[data-store^="product-item-image-"]` | imagen con hook oficial | `grid/item.tpl` | Alta | anchor estable para overflow y posicion |
| `[data-store="product-item-labels"]` | wrapper de badges/labels en card | `grid/item.tpl` | Alta | posicion absoluta sobre la imagen |
| `[data-store="product-item-label-shipping"]` | label de envio gratis en card | `grid/item.tpl` | Alta | tipografia y posicion seguras |
| `.item-description .btn-primary`, `.btn-small`, `.btn-link` | variaciones de CTA en card | Bootstrap + theme | Media | cubiertos como fallback junto al CTA principal |

### Home image-text module

| Selector actual | Que parece representar | Respaldo documental | Estabilidad | Observacion |
| --- | --- | --- | --- | --- |
| `[data-store="home-image-text-module"]` | bloque imagen + texto en home | puntos de anclaje oficiales | Alta | anchor oficial de Morelia |
| `.textbanner-paragraph` | parrafo descriptivo del modulo | theme Morelia | Media | tipografia y layout seguros |
| `.textbanner-text` | contenedor del area de texto | theme Morelia | Media | height ajustado a auto |
| `.js-textbanner-image-container`, `.textbanner-image` | wrapper de la imagen | theme Morelia | Media | overflow y fondo seguros |
| `.js-textbanner-image` | imagen del modulo | theme Morelia | Media | object-fit y transicion seguros |
| `.js-textbanner-text` | wrapper de texto con layout flex | theme Morelia | Media | padding y alineacion seguros |
| `.js-banner-title`, `.textbanner-text h3` | titulo del modulo | theme Morelia | Media | tipografia segura |
| `.placeholder-banner` | placeholder visual cuando no hay contenido | theme Morelia | Baja | oculto intencionalmente |

## Categorias / subcategorias / listados

### Hooks validados en preview durante la implementacion

Los siguientes scopes quedaron validados como compatibles con la unificacion visual de cards y listados. No todos necesariamente aparecen a la vez, pero ya fueron contemplados como grupo de trabajo real sobre la tienda:

- `.js-products-grid`
- `.products-grid`
- `.product-table`
- `.js-product-table`
- `.js-category-products`
- `[data-store="category-products"]`
- `[data-store="products-list"]`
- `[data-store="search-results"]`

Lectura practica:

- Para futuras iteraciones de grilla/listado, conviene empezar por estos scopes antes de inventar wrappers nuevos.
- Dentro de esos scopes, la familia `.item-*` y los hooks `data-store="product-item-*"` ya demostraron ser el camino mas consistente.

### Sidebar / filtros / navegacion interna

Los siguientes wrappers quedaron aceptados como capa de compatibilidad para navegacion lateral, filtros y facets:

- `.js-products-sidebar`
- `.js-filters-container`
- `.js-products-filters`
- `.sidebar-filters`
- `.filters-container`
- `.category-sidebar`
- `.collection-sidebar`
- `.js-products-categories`
- `.js-category-sidebar`

Estabilidad:

- `Media` como wrappers visuales.
- Son utiles para tipografia, spacing, bordes y estados activos.
- No conviene asumir que controlan comportamiento JS; sirven como scope visual, no como contrato funcional.

### Paginacion y controles de listado

Wrappers contemplados para mantener consistencia visual en listados:

- `.pagination`
- `.js-pagination`
- `.pagination-container`
- `.js-pagination-container`
- `.pager`
- `.js-pager`
- `.sort-by`
- `.js-sort-by`
- `.js-view-change`
- `.js-products-order-by`
- `.js-products-controls`
- `.products-controls`

Estabilidad:

- `Media` para paginacion y sorting.
- Seguros para tipografia, border, hover y spacing.
- Evitar cambiar display estructural o logica de visibilidad sin validar comportamiento del theme.

## Mobile

El CSS incluye un bloque `@media (max-width: 768px)` que ajusta tipografia, spacing y dimensiones para mobile. Afecta:

- Navbar: barra informativa, logo y navegacion mobile.
- Detalle de producto: titulo, variantes, precio y textos secundarios.
- Quickshop: nombre, precio, variantes, cantidad y CTA.
- Home image-text module: imagen, texto y titulo.
- Grilla: nombres, precios, CTAs y spacing de cards.
- Sidebar/filtros: titulos, links y labels.
- Paginacion: dimensiones y tipografia.

No cambia el orden visual ni la arquitectura de selectores; solo reduce tamaños y ajusta espaciados para pantallas angostas.

## Relacion directa con docs oficiales

### Bloques del CSS actual fuertemente respaldados

- `#single-product`
- `.page-header`
- `.breadcrumbs`
- `[data-store^="product-name-"]`
- `.price-container`
- `#price_display`
- `.js-price-display`
- `.js-product-payments-container`
- `.js-product-variants-group`
- `.js-quantity-*`
- `.product-description`
- `.section-featured-home`
- `[data-store="home-image-text-module"]`
- `.js-products-grid`
- `.products-grid`
- `[data-store="category-products"]`
- `[data-store="products-list"]`
- `[data-store="search-results"]`
- `[data-store="product-item-labels"]`
- `[data-store="product-item-label-shipping"]`
- `[data-store^="product-item-image-"]`
- `.item-name`
- `.item-price-container`
- `[data-store="product-item-buy-button"]`

### Hooks validos pero mas sensibles

- `.head-info`, `.js-head-info`, `.js-informative-banner`
- `.head-main`, `.js-head-main`
- `.utilities-container`, `.js-utilities-container`
- `.nav-desktop`, `.js-nav-desktop`, `.desktop-nav`
- `.desktop-list-subitems`
- `.js-search-input`
- `.js-mobile-nav`, `.mobile-nav`, `.js-nav-mobile`
- `.btn-variant`
- `.btn-variant-color`
- `.js-shipping-add-product-label`
- `.js-product-form-free-shipping-message`
- `.js-shipping-minimum-label`
- `.js-free-shipping-discount-not-combinable`
- `.js-accordion-toggle`

## Reglas practicas para editar este archivo sin romper cosas

### Seguro

- cambiar color
- cambiar letter-spacing
- cambiar text-transform
- ajustar margin/padding
- ajustar border y background
- hover suave en imagenes y botones

### Cuidado medio

- cambiar `display` en wrappers de shipping o payments
- fijar alturas en mensajes dinamicos
- reordenar flex de variantes o cantidad
- tocar opacidad en estados selected/disabled

### Riesgo alto

- ocultar `.js-price-display`
- ocultar `.js-product-payments-container`
- cambiar interaccion visual de `.js-quantity-*`
- colapsar `.js-shipping-*`
- romper el area clickable de `.item-link`

## Recomendacion de selector para futuras iteraciones

Priorizar esta jerarquia:

1. `#single-product[data-store="product-detail"]`
2. `.section-featured-home`
3. `[data-store^="product-name-"]`, `[data-store^="product-item-name-"]`, `[data-store^="product-item-price-"]`, `[data-store="product-buy-button"]`, `[data-store="product-item-buy-button"]`
4. clases documentadas del componente
5. clases `js-...` solo cuando no haya mejor hook

## Regla de implementacion ya validada

Para paginas de categoria, subcategoria, coleccion y busqueda, el orden de decision que ya funciono en esta tienda es:

1. Scope de listado validado en preview (`.js-products-grid`, `.products-grid`, `.product-table`, `[data-store="category-products"]`, `[data-store="products-list"]`, `[data-store="search-results"]`)
2. Hooks oficiales de item (`[data-store^="product-item-name-"]`, `[data-store^="product-item-price-"]`, `[data-store="product-item-buy-button"]`, `[data-store="product-item-buy-now"]`)
3. Clases `.item-*` como soporte estructural
4. Wrappers de sidebar/filtros/paginacion como capa visual secundaria

Regla operativa:

- Si un cambio de grilla no entra por ese orden, hay que asumir que todavia falta evidencia y conviene inspeccionar preview antes de seguir.
- Esto baja bastante el riesgo de alucinacion porque obliga a partir de hooks ya comprobados en la tienda real.

## Conclusiones

- El CSS actual esta razonablemente bien anclado para seguir evolucionando.
- La mayor parte de sus selectores coinciden con componentes documentados de Base/Snipplets.
- El principal foco de cuidado esta en variantes, precio, cuotas y shipping, no en la parte puramente visual.
# Mapa de selectores del CSS actual

## Objetivo

Traducir los selectores usados hoy en `theme.css` a su significado funcional y a su nivel de respaldo documental.

## Leyenda de estabilidad

- Alta: selector o hook explicitamente respaldado por docs oficiales.
- Media: aparece alineado con patrones oficiales, pero puede variar entre themes o customizaciones.
- Baja: parece mas dependiente del marcado puntual del theme o de una capa visual no documentada.

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
- `.item-name`
- `.item-price-container`
- `[data-store="product-item-buy-button"]`

### Hooks validos pero mas sensibles

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

## Conclusiones

- El CSS actual esta razonablemente bien anclado para seguir evolucionando.
- La mayor parte de sus selectores coinciden con componentes documentados de Base/Snipplets.
- El principal foco de cuidado esta en variantes, precio, cuotas y shipping, no en la parte puramente visual.
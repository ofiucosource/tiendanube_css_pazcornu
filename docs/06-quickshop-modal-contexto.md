# Contexto de quickshop modal

## Objetivo

Registrar la estructura HTML observada en `#quickshop-modal` para poder intervenirla con CSS de forma precisa, distinguiendo:

- etiquetas HTML reales
- ids y clases disponibles
- anchors mas estables para estilado
- hooks sensibles porque probablemente estan conectados a JS

## Alcance de este documento

Este archivo describe el DOM del quickshop a partir del `outerHTML` provisto, no una taxonomia universal de todos los quickshops posibles de Morelia.

Lectura correcta:

1. sirve como snapshot operativo del modal actual
2. ayuda a abrir selectores mas precisos en `theme.css`
3. no garantiza que todos los productos o estados rendericen markup identico

## Scope principal

El modal entero queda envuelto por este nodo:

- `div#quickshop-modal.js-modal.js-fullscreen-modal.modal.modal-quickshop.bottom.modal-overflow-none.modal-bottom.modal--md.transition-slide.modal-centered-md.modal-centered-medium.transition-soft.modal-show.in`

Implicancia CSS:

- `#quickshop-modal` es el mejor scope raiz para cualquier override visual del quickshop.
- `.modal-quickshop` sirve como fallback si el id cambiara o si hubiera mas de una instancia equivalente.
- las clases `js-modal`, `js-fullscreen-modal` y `js-modal-close` deben tratarse como sensibles a comportamiento.

## Arbol estructural del modal

```text
div#quickshop-modal
  div.modal-header.js-modal-close.js-fullscreen-modal-close.modal-sticky-close.modal-header-no-title.d-md-none
    div.row.no-gutters.align-items-center
      div.col.d-none.d-md-block.pr-3.pl-5
      div.col-auto
        a.js-modal-close.modal-close.pr-md-0
          svg.icon-inline.svg-icon-text
            use

  div.modal-body.modal-scrollable.pt-4.px-0.px-md-4
    div.js-item-product.modal-scrollable.modal-scrollable-area.js-swiper-slide-visible.js-item-slide
      div.js-product-container.js-quickshop-container.js-quickshop-modal.js-quickshop-modal-shell
        div.row.no-gutters

          div.col-md-6.mb-1.px-4.px-md-0
            div.quickshop-image-container
              div.js-quickshop-image-padding
                img.js-item-image.js-quickshop-img.quickshop-image.img-absolute-centered

          div.js-item-variants.col-md-6.pt-3.px-4.pb-4.mt-md-1.pt-md-2.pr-md-3
            div.row.no-gutters.align-items-center.mt-md-0.mr-md-1.mb-2
              div.col
                div.js-item-name.h4.h2-md.text-center.text-md-left
              div.col-auto.d-none.d-md-block
                a.js-modal-close.modal-close.pr-0
                  svg.icon-inline.svg-icon-text
                    use

            div.mb-4.mr-md-1.text-center.text-md-left
              span.js-price-display
              span.js-compare-price-display.price-compare

            div#quickshop-form.mr-md-1
              form.js-product-form
                input[type="hidden"][name="add_to_cart"]

                div.js-product-variants.js-product-quickshop-variants.form-row
                  div.js-product-variants-group.js-color-variants-container.form-group.col-12.text-center.text-md-left.mb-2[data-variation-id="0"]
                    div.form-group.d-none
                      label.form-label
                      select#variation_1.form-select.js-variation-option.js-refresh-installment-data
                        option
                      div.form-select-icon
                        svg.icon-inline.icon-w-14.icon-rotate-90
                          use
                    label.form-label.text-center.text-md-left
                      span.js-insta-variation-label
                    a.js-insta-variant.btn.btn-variant.selected.btn-variant-color.p-0[data-option="Negro"]
                      span.btn-variant-content

                  div.js-product-variants-group.form-group.col-12.text-center.text-md-left.mb-4[data-variation-id="1"]
                    div.form-group.d-none
                      label.form-label
                      select#variation_2.form-select.js-variation-option.js-refresh-installment-data
                        option
                      div.form-select-icon
                        svg.icon-inline.icon-w-14.icon-rotate-90
                          use
                    label.form-label.text-center.text-md-left
                      span.js-insta-variation-label
                    a.js-insta-variant.btn.btn-variant.selected[data-option="Small"]
                      span.btn-variant-content
                    a.js-insta-variant.btn.btn-variant[data-option="Medium"]
                      span.btn-variant-content
                    a.js-insta-variant.btn.btn-variant[data-option="Large"]
                      span.btn-variant-content

                div.row
                  div.js-product-quantity-container.col-4.pr-0.pr-md-3
                    div.form-group.js-quantity
                      div.form-quantity.form-quantity-product.d-flex.form-row.m-0.align-items-center[data-component="product.quantity"]
                        span.js-quantity-down.form-quantity-icon.btn.icon-35px.font-small[data-component="product.quantity.minus"]
                          svg.icon-inline
                            use
                        div.form-control-container.col.px-0[data-component="product.adding-amount"]
                          input.js-quantity-input.form-control.form-control-big.form-control-inline[type="number"]
                        span.js-quantity-up.form-quantity-icon.btn.icon-35px.font-small[data-component="product.quantity.plus"]
                          svg.icon-inline
                            use

                  div.js-buy-button-container.col-8.pl-md-0.buy-button-container
                    input.js-addtocart.js-prod-submit-form.btn-add-to-cart.btn.btn-primary.btn-big.w-100.cart[type="submit"]
                    div.js-addtocart.js-addtocart-placeholder.btn.btn-primary.btn-block.btn-transition.btn-big.disabled
                      div.d-inline-block
                        span.js-addtocart-text
                        span.js-addtocart-success.transition-container
                          svg.icon-inline.font-body
                            use
                        div.js-addtocart-adding.transition-container.transition-icon
                          span.js-addtocart-adding-text
                          svg.icon-inline.icon-spin.icon-w-2em.ml-1
                            use

            div#stock-notification-container.morelia
              div#stock-notification-request-message
              dialog#stock-notification-modal-dialog.morelia
                span#stock-notification-close-button
                div.stock-notification-intro-message
                div#stock-notification-product-name
                form#stock-notification-form
                  span
                    input#stock-notification-email[type="email"]
                  input#stock-notification-submit[type="submit"]
                div#stock-notification-success-message
                div.stock-notification-powered-by
                  a
```

## Mapa por bloques

## 1. Contenedor raiz y shell del modal

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| modal raiz | `div` | `#quickshop-modal` | scope principal del popup | Alta |
| header mobile | `div` | `.modal-header.modal-sticky-close` | cierre superior en mobile | Media |
| body scrollable | `div` | `.modal-body.modal-scrollable` | contenedor del contenido | Media |
| slide/item | `div` | `.js-item-product` | wrapper del producto cargado | Media |
| shell interno | `div` | `.js-product-container.js-quickshop-container` | scope principal del contenido del producto | Media |

Notas:

- `#quickshop-modal` es el anchor mas claro para limitar cualquier override.
- `.js-item-product`, `.js-product-container`, `.js-quickshop-container` y `.js-quickshop-modal-shell` parecen asociados a logica de quickshop y cambio de producto.

## 2. Cierre del modal

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| boton cerrar mobile | `a` | `.js-modal-close.modal-close.pr-md-0` | icono dentro del header mobile |
| boton cerrar desktop | `a` | `.js-modal-close.modal-close.pr-0` | aparece junto al nombre del producto |
| icono cerrar | `svg` | `.icon-inline.svg-icon-text` | icono reusable |

Regla operativa:

- se puede estilizar color, size, padding y hover de `.modal-close`
- no conviene ocultar ni bloquear `.js-modal-close`

## 3. Columna de imagen

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| columna imagen | `div` | `.col-md-6.mb-1.px-4.px-md-0` | mitad izquierda del modal | Media |
| wrapper imagen | `div` | `.quickshop-image-container` | caja visual de la imagen | Media |
| padding helper | `div` | `.js-quickshop-image-padding` | reserva de proporcion/espacio | Baja |
| imagen | `img` | `.js-item-image.js-quickshop-img.quickshop-image.img-absolute-centered` | imagen del producto | Media |

Regla operativa:

- para bordes, fondo, overflow y relacion visual, conviene anclar en `.quickshop-image-container`
- para `object-fit`, escala, transicion o posicionamiento fino, conviene anclar en `.quickshop-image`
- `img-absolute-centered` y `js-quickshop-image-padding` sugieren una logica de centrado sensible

## 4. Columna de informacion

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| columna info | `div` | `.js-item-variants.col-md-6...` | mitad derecha del modal | Media |
| fila header | `div` | `.row.no-gutters.align-items-center...` | nombre + close desktop | Baja |
| nombre producto | `div` | `.js-item-name.h4.h2-md` | titulo visible del producto | Media |
| bloque precio | `div` | `[data-store="product-item-price-"]` | wrapper del precio | Alta |
| precio actual | `span` | `.js-price-display` | precio reactivo | Alta |
| precio compare | `span` | `.js-compare-price-display.price-compare` | tachado/promocion | Media |

Notas:

- aunque el nombre no expone `data-store` en el wrapper visible, si trae `data-store="product-item-name-"` en el mismo nodo.
- el precio tiene un `data-store` parcial visible en el wrapper, util si el id se completa en runtime.

## 5. Formulario de compra

Nodo principal:

- `div#quickshop-form > form.js-product-form`

Elementos confirmados:

| Bloque | Etiqueta | Selector visible | Funcion |
| --- | --- | --- | --- |
| contenedor del form | `div` | `#quickshop-form` | scope directo del formulario |
| formulario | `form` | `.js-product-form` | submit de compra |
| input hidden | `input` | `input[name="add_to_cart"]` | id de producto base |
| grid de variantes | `div` | `.js-product-variants.js-product-quickshop-variants.form-row` | grupo de opciones |

Regla operativa:

- `#quickshop-form` es un muy buen scope local para tipografia, spacing y componentes del form.
- `.js-product-form` y `.js-product-variants` son hooks probablemente usados por JS.

## 6. Variantes

Cada variante vive dentro de:

- `div.js-product-variants-group.form-group[data-variation-id]`

Estructura repetida:

1. `div.form-group.d-none`
2. `label.form-label`
3. `select.form-select.js-variation-option.js-refresh-installment-data`
4. `div.form-select-icon > svg`
5. `label.form-label` visible con `span.js-insta-variation-label`
6. una o varias `a.js-insta-variant.btn.btn-variant`
7. dentro de cada opcion, `span.btn-variant-content`

### Variante color

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| grupo color | `div` | `.js-color-variants-container[data-variation-id="0"]` | wrapper especifico de color |
| select oculto | `select` | `#variation_1` | fallback nativo |
| label visible | `label` | `.form-label` | texto `Color:` |
| boton swatch | `a` | `.js-insta-variant.btn.btn-variant.selected.btn-variant-color` | selector visual |
| contenido del swatch | `span` | `.btn-variant-content` | color inline en `style` |

### Variante talle

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| grupo talle | `div` | `.js-product-variants-group[data-variation-id="1"]` | wrapper de talle |
| select oculto | `select` | `#variation_2` | fallback nativo |
| label visible | `label` | `.form-label` | texto `Talle:` |
| opcion seleccionada | `a` | `.js-insta-variant.btn.btn-variant.selected` | estado activo |
| opcion normal | `a` | `.js-insta-variant.btn.btn-variant` | botones de talle |
| contenido textual | `span` | `.btn-variant-content` | texto Small, Medium, Large |

Regla operativa:

- para layout y spacing, usar `.js-product-variants-group`, `.form-label`, `.btn-variant`, `.btn-variant-color`
- para estados, usar `.selected`, `:hover`, `:focus-visible`
- no ocultar `select.js-variation-option` aunque hoy este dentro de `.d-none`

## 7. Cantidad

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| columna cantidad | `div` | `.js-product-quantity-container.col-4` | ancho del modulo cantidad | Media |
| grupo cantidad | `div` | `.form-group.js-quantity` | wrapper del control | Media |
| control cantidad | `div` | `.form-quantity.form-quantity-product` | layout del stepper | Media |
| restar | `span` | `.js-quantity-down.form-quantity-icon.btn` | decremento | Alta |
| input numerico | `input` | `.js-quantity-input.form-control` | valor editable | Alta |
| sumar | `span` | `.js-quantity-up.form-quantity-icon.btn` | incremento | Alta |

Regla operativa:

- se pueden ajustar bordes, altura, ancho, tipografia y estados hover/focus
- no conviene tocar semantica interactiva ni esconder los controles `js-quantity-*`

## 8. CTA de compra

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| columna CTA | `div` | `.js-buy-button-container.col-8.buy-button-container` | wrapper del boton principal | Media |
| submit real | `input` | `.js-addtocart.js-prod-submit-form.btn-add-to-cart.btn.btn-primary.btn-big.w-100.cart` | agregar al carrito | Alta |
| placeholder | `div` | `.js-addtocart.js-addtocart-placeholder...disabled` | estados agregando/listo | Alta |
| texto base | `span` | `.js-addtocart-text` | label normal | Media |
| exito | `span` | `.js-addtocart-success` | feedback success | Media |
| estado cargando | `div` | `.js-addtocart-adding` | feedback loading | Media |

Regla operativa:

- estilado seguro en `.btn-add-to-cart`, `.buy-button-container`, `.js-addtocart-placeholder`
- no conviene eliminar el placeholder porque participa del feedback de compra

## 9. Bloque de stock notification

Este bloque parece custom y no parte del quickshop nativo estricto.

Estructura:

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| contenedor | `div` | `#stock-notification-container.morelia` | scope principal del modulo |
| trigger textual | `div` | `#stock-notification-request-message` | CTA para abrir aviso |
| modal interno | `dialog` | `#stock-notification-modal-dialog.morelia` | popup secundario |
| cierre | `span` | `#stock-notification-close-button` | boton cerrar |
| intro | `div` | `.stock-notification-intro-message` | copy de entrada |
| nombre producto | `div` | `#stock-notification-product-name` | texto dinamico |
| form | `form` | `#stock-notification-form` | captura email |
| email | `input` | `#stock-notification-email[type="email"]` | campo email |
| submit | `input` | `#stock-notification-submit[type="submit"]` | CTA envio |
| success | `div` | `#stock-notification-success-message` | mensaje de exito |
| creditos | `div` | `.stock-notification-powered-by` | attribution/app link |

Implicancia CSS:

- este bloque si tiene varios ids muy convenientes para overrides puntuales
- al estar dentro de `#quickshop-modal`, se puede limitar todo con `#quickshop-modal #stock-notification-container`

## Inventario de etiquetas HTML presentes

Etiquetas confirmadas en este snapshot del quickshop:

- `div`
- `a`
- `svg`
- `use`
- `img`
- `form`
- `input`
- `label`
- `select`
- `option`
- `span`
- `dialog`

Lectura practica:

- la mayor parte del layout descansa en `div`
- la interaccion visual de variantes no usa `button`, usa `a`
- el CTA principal es `input[type="submit"]`, no `button`
- el modulo de aviso de stock usa `dialog`, lo cual cambia bastante respecto de un `div` modal comun

## Selectores recomendados para CSS

Prioridad sugerida:

1. `#quickshop-modal`
2. `#quickshop-modal #quickshop-form`
3. `#quickshop-modal .quickshop-image-container`
4. `#quickshop-modal .js-item-name[data-store="product-item-name-"]`
5. `#quickshop-modal [data-store="product-item-price-"]`
6. `#quickshop-modal .js-product-variants-group`
7. `#quickshop-modal .btn-variant`
8. `#quickshop-modal .form-quantity-product`
9. `#quickshop-modal .btn-add-to-cart`
10. `#quickshop-modal #stock-notification-container`

## Hooks sensibles

Conviene tratar como sensibles estos hooks:

- `.js-modal-close`
- `.js-item-product`
- `.js-product-container`
- `.js-quickshop-container`
- `.js-quickshop-modal`
- `.js-quickshop-modal-shell`
- `.js-product-form`
- `.js-product-variants`
- `.js-variation-option`
- `.js-refresh-installment-data`
- `.js-insta-variant`
- `.js-quantity-down`
- `.js-quantity-up`
- `.js-quantity-input`
- `.js-addtocart`

Regla practica:

- se pueden usar para estilado cuando no exista mejor anchor
- no conviene basar toda la arquitectura CSS en ellos si hay ids, `data-store` o clases visuales mas limpias

## Cambios visuales de bajo riesgo

- padding y gap de columnas internas
- tipografia del nombre y precio
- borde, radio y fondo de `.quickshop-image-container`
- apariencia de `.btn-variant` y `.btn-variant-color`
- apariencia del stepper de cantidad
- altura, peso visual y hover del boton principal
- layout y look del bloque `#stock-notification-container`

## Cambios con mas cuidado

- alterar `display` del shell principal del modal
- reposicionar cierres si se rompe la usabilidad mobile o desktop
- ocultar `select` o inputs que hoy operan como fallback del JS
- convertir anchors de variantes en layouts muy distintos sin validar seleccion y stock
- romper el placeholder de add to cart o sus estados internos
- tocar `dialog` sin revisar apertura, cierre y focus

## Conclusiones operativas

- `#quickshop-modal` ya da un scope suficientemente fuerte para intervenir el quickshop sin contaminar otras vistas.
- el modal mezcla clases visuales utiles con muchos hooks `js-*`, asi que conviene separar selectores de estilo de selectores de comportamiento.
- la parte mas segura para CSS esta en imagen, tipografia, variantes visibles, cantidad, CTA y bloque custom de stock notification.
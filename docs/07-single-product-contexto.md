# Contexto de single product

## Objetivo

Registrar la estructura HTML observada en `#single-product` para poder intervenirla con CSS sin romper piezas sensibles del detalle de producto.

Este documento separa:

- etiquetas HTML efectivamente presentes
- bloques estructurales del product detail
- anchors estables para CSS
- hooks sensibles porque probablemente estan conectados a JS o a actualizaciones dinamicas

## Alcance de este documento

Este archivo describe el `outerHTML` puntual provisto para `#single-product`, no una garantia absoluta de todos los estados posibles del product detail en Morelia.

Lectura correcta:

1. funciona como snapshot operativo del detalle actual
2. sirve para decidir selectores en `theme.css`
3. debe convivir con `05-taxonomia-html-tiendanube-morelia.md` y `02-mapa-selectores-theme-actual.md`

## Scope principal

Nodo raiz observado:

- `div#single-product.js-has-new-shipping.js-product-detail.js-product-container.js-shipping-calculator-container.pb-4.pt-md-4.pb-md-3[data-store="product-detail"]`

Implicancia CSS:

- `#single-product[data-store="product-detail"]` es el mejor scope raiz para cualquier override del detalle.
- `data-store="product-detail"` es el anchor mas estable del bloque completo.
- `.js-product-detail`, `.js-product-container` y `.js-shipping-calculator-container` parecen hooks de comportamiento.

## Arbol estructural resumido

```text
div#single-product[data-store="product-detail"]
  div.container
    div.row
      div.col-md-7
        div.row[data-store="product-image-301455005"]
          div.col-md-auto.d-none.d-md-block
            div.product-thumbs-container
              div.js-swiper-product-thumbs
                div.swiper-wrapper
                  div.swiper-slide
                    a.js-product-thumb.product-thumb
                      img
              div.text-center.d-none.d-md-block
                div.js-swiper-product-thumbs-prev
                  svg
                div.js-swiper-product-thumbs-next
                  svg

          div.col.px-3
            div.js-swiper-product.swiper-container.product-detail-slider
              div.labels.js-labels-floating-group[data-store="product-item-labels"]
                div.js-stock-label-private[data-store="product-item-label-stock"]
                div.js-offer-label-private[data-store="product-item-offer-label"]
                  span.label-offer-percentage
                  span.label-offer-percentage-text
                div.js-shipping-label-private[data-store="product-item-label-shipping"]
              span.hidden[data-store="stock-product-301455005-9"]
              span.js-free-shipping-combines-config.hidden
              div.swiper-wrapper
                div.js-product-slide.swiper-slide
                  a.js-product-slide-link[data-fancybox="product-gallery"]
                    img.js-product-slide-img.product-slider-image
              div.row.no-gutters.d-md-none
                div.js-swiper-product-prev
                  svg
                div.js-swiper-product-pagination
                div.js-swiper-product-next
                  svg
              div.text-center.d-none.d-md-block.mt-4
                a.social-share-button
                  svg
                div.pinterest-hidden.social-share-button
                  a

      div.col[data-store="product-info-301455005"]
        div.pt-md-3
          section.page-header[data-store="page-title"]
            div.breadcrumbs
              a.crumb
              span.separator
              span.crumb.active
            h1.js-product-name[data-store="product-name-301455005"]

          div.price-container[data-store="product-price-301455005"]
            div.js-price-container
              span
                div.js-price-display#price_display
              span
                div.js-compare-price-display#compare_price_display.price-compare
              div.js-price-without-taxes-container.price-without-taxes-container
                span.price-without-taxes-label
                span.js-price-without-taxes.price-without-taxes

            div.js-modal-open.js-fullscreen-modal-open.js-product-payments-container
              div.js-max-installments-container
                div.js-max-installments.product-installments
                  span.js-installment-amount
                  span.js-installment-price
              div.js-product-discount-container
                div.js-product-discount-disclaimer
              a#btn-installments.btn-link

            div.js-free-shipping-minimum-message.free-shipping-message
              span.text-accent
              span.js-shipping-minimum-label
              div.js-free-shipping-discount-not-combinable

          form#product_form.js-product-form[data-store="product-form-301455005"]
            input[type="hidden"][name="add_to_cart"]
            div.js-product-variants.form-row
              div.js-product-variants-group.js-color-variants-container[data-variation-id="0"]
                div.form-group.d-none
                  label.form-label
                  select#variation_1.form-select.js-variation-option.js-refresh-installment-data
                  div.form-select-icon
                    svg
                label.form-label
                  span.js-insta-variation-label
                a.js-insta-variant.btn.btn-variant.btn-variant-color.selected
                  span.btn-variant-content

              div.js-product-variants-group[data-variation-id="1"]
                div.form-group.d-none
                  label.form-label
                  select#variation_2.form-select.js-variation-option.js-refresh-installment-data
                  div.form-select-icon
                    svg
                label.form-label
                  span.js-insta-variation-label
                a.js-insta-variant.btn.btn-variant.selected
                  span.btn-variant-content
                a.js-insta-variant.btn.btn-variant
                  span.btn-variant-content

            div.js-last-product

            div.row.mb-4
              div.js-product-quantity-container
                div.form-group.js-quantity
                  div.form-quantity.form-quantity-product[data-component="product.quantity"]
                    span.js-quantity-down[data-component="product.quantity.minus"]
                      svg
                    div.form-control-container[data-component="product.adding-amount"]
                      input.js-quantity-input[type="number"]
                    span.js-quantity-up[data-component="product.quantity.plus"]
                      svg

              div.js-buy-button-container
                input.js-addtocart.js-prod-submit-form.btn-add-to-cart[data-store="product-buy-button"][data-component="product.add-to-cart"][type="submit"]
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
                div.js-addtocart.js-addtocart-placeholder
                  div.d-inline-block
                    span.js-addtocart-text
                    span.js-addtocart-success
                      svg
                    div.js-addtocart-adding
                      span.js-addtocart-adding-text
                      svg

              div.col-12
                div.js-added-to-cart-product-message
                  a.js-modal-open.js-open-cart.js-fullscreen-modal-open

              div.js-shipping-add-product-label
                span.js-fs-add-this-product
                span.js-fs-add-one-more
                span.text-accent

              div.js-product-form-free-shipping-message.js-free-shipping-message

        div#installments-modal.js-modal.js-fullscreen-modal.modal
          div.js-modal-close.js-fullscreen-modal-close.modal-header
            div.row.no-gutters.align-items-center
              div.col
              div.col-auto
                a.js-modal-close.modal-close
                  svg
          div.modal-body.modal-scrollable
            div.modal-scrollable.modal-scrollable-area
              div.js-tab-container
                ul.js-payments-tab-group.tab-group
                  li.js-installments-gw-tab.js-tab.tab
                    a.js-tab-link.tab-link
                      span.js-modal-tab-discount
                div.js-tabs-content.tab-content
                  div.js-tab-panel.tab-panel.js-gw-tab-pane
                    div.js-payment-method-title
                    div.js-info-payment-method-container.box
                      div.js-payment-method-discount
                      div.js-payment-method-total
                      div.js-discount-explanation
                      div.js-discount-disclaimer
                      table.js-payments-table.table
                        tbody
                          tr.js-payment-provider-installments-row
                            td
                              span.js-installment-amount
                              span.js-installment-price
                            td
                              small
                            td.text-right
                              span.js-installment-total-price
          div.modal-footer
            span.js-modal-close.js-fullscreen-modal-close.btn-link

        div.js-modal-overlay.modal-overlay

        div[data-store="product-description-301455005"]
          div.user-content
            p
          div#reviewsapp

    div.text-center.d-md-none
      a.social-share-button
        svg
      div.pinterest-hidden.social-share-button
        a
```

## Mapa por bloques

## 1. Contenedor raiz y layout general

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| raiz del detalle | `div` | `#single-product[data-store="product-detail"]` | scope principal del product detail | Alta |
| container interno | `div` | `.container` | ancho general del contenido | Media |
| fila principal | `div` | `.row` | divide media y contenido | Media |
| columna media | `div` | `.col-md-7` | galeria, labels y share desktop | Media |
| columna info | `div` | `[data-store="product-info-301455005"]` | header, precio, form, cuotas y descripcion | Alta |

Regla operativa:

- para overrides del detalle completo, arrancar por `#single-product[data-store="product-detail"]`
- para targeting fino del bloque derecho, preferir `data-store="product-info-*"`

## 2. Galeria de producto

### Thumbnails desktop

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| wrapper thumbs | `div` | `.product-thumbs-container` | caja lateral de miniaturas | Media |
| carrusel thumbs | `div` | `.js-swiper-product-thumbs` | slider vertical | Media |
| slide thumb | `div` | `.swiper-slide` | item del slider | Baja |
| thumb clickable | `a` | `.js-product-thumb.product-thumb` | cambia imagen activa | Media |
| imagen thumb | `img` | `.img-absolute.img-absolute-centered` | miniatura cargada | Baja |
| control prev | `div` | `.js-swiper-product-thumbs-prev` | navegacion arriba | Media |
| control next | `div` | `.js-swiper-product-thumbs-next` | navegacion abajo | Media |

### Slider principal

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| slider principal | `div` | `.js-swiper-product.product-detail-slider` | carrusel de imagenes | Media |
| grupo labels | `div` | `.labels.js-labels-floating-group[data-store="product-item-labels"]` | badges flotantes | Alta |
| label stock | `div` | `[data-store="product-item-label-stock"]` | estado sin stock | Alta |
| label promo | `div` | `[data-store="product-item-offer-label"]` | porcentaje off | Alta |
| label shipping | `div` | `[data-store="product-item-label-shipping"]` | envio gratis | Alta |
| slide principal | `div` | `.js-product-slide.swiper-slide` | item de imagen | Media |
| link fancybox | `a` | `.js-product-slide-link` | abre lightbox | Media |
| imagen principal | `img` | `.js-product-slide-img.product-slider-image` | imagen de producto | Media |
| nav mobile prev | `div` | `.js-swiper-product-prev` | control mobile | Media |
| paginacion mobile | `div` | `.js-swiper-product-pagination` | estado del slider | Media |
| nav mobile next | `div` | `.js-swiper-product-next` | control mobile | Media |

Regla operativa:

- para bordes, fondos, espaciados y look general, anclar en `.product-thumbs-container`, `.product-detail-slider` y `.product-thumb`
- para labels, usar `data-store="product-item-label-*"`
- evitar cambiar `display`, `overflow` o posicionamiento estructural de wrappers `swiper-*` sin validar el slider

## 3. Social share

Hay dos bloques separados:

1. bloque desktop dentro de la columna media
2. bloque mobile al final de `#single-product`

Elementos presentes:

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| boton share | `a` | `.social-share-button` | whatsapp, facebook, twitter, pinterest |
| pinterest helper | `div` | `.pinterest-hidden.social-share-button` | contenedor oculto |
| pinterest save | `a` | `.PIN_..._save` | generado por Pinterest |

Regla operativa:

- `.social-share-button` es suficiente para look visual general
- evitar depender de clases `PIN_*` porque parecen generadas dinamicamente

## 4. Header del producto

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| header | `section` | `.page-header[data-store="page-title"]` | titulo + breadcrumbs | Alta |
| breadcrumbs | `div` | `.breadcrumbs` | navegacion jerarquica | Alta |
| crumb link | `a` | `.crumb` | enlace de jerarquia | Media |
| separator | `span` | `.separator` | separador visual | Media |
| crumb activo | `span` | `.crumb.active` | pagina actual | Media |
| titulo | `h1` | `.js-product-name[data-store="product-name-301455005"]` | nombre visible del producto | Alta |

Regla operativa:

- `data-store="page-title"` y `data-store="product-name-*"` son anchors fuertes para tipografia, espaciado y jerarquia

## 5. Precio, cuotas y shipping promo

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| contenedor precio | `div` | `.price-container[data-store="product-price-301455005"]` | bloque completo de pricing | Alta |
| wrapper reactivo | `div` | `.js-price-container` | precio principal y compare | Media |
| precio principal | `div` | `#price_display.js-price-display` | precio actualizado por variante | Alta |
| compare price | `div` | `#compare_price_display.js-compare-price-display.price-compare` | precio tachado | Alta |
| precio sin impuestos | `div` | `.js-price-without-taxes-container.price-without-taxes-container` | info fiscal secundaria | Media |
| label impuestos | `span` | `.price-without-taxes-label` | copy secundaria | Media |
| valor sin impuestos | `span` | `.js-price-without-taxes.price-without-taxes` | valor dinamico | Media |
| cuotas / pagos | `div` | `.js-product-payments-container` | resumen de cuotas + acceso al modal | Alta |
| max installments | `div` | `.js-max-installments.product-installments` | mensaje de cuotas | Media |
| cantidad cuotas | `span` | `.js-installment-amount` | numero de cuotas | Media |
| valor cuota | `span` | `.js-installment-price.product-installment-value` | importe cuota | Media |
| descuento pago | `div` | `.js-product-discount-container` | promo por medio de pago | Media |
| disclaimer promo | `div` | `.js-product-discount-disclaimer` | no acumulable | Alta |
| link detalles | `a` | `#btn-installments.btn-link` | abre modal de medios de pago | Media |
| envio gratis | `div` | `.js-free-shipping-minimum-message.free-shipping-message` | promo de shipping | Media |
| minimo shipping | `span` | `.js-shipping-minimum-label` | umbral dinamico | Media |
| disclaimer shipping | `div` | `.js-free-shipping-discount-not-combinable` | no combinable | Media |

Regla operativa:

- `#price_display`, `#compare_price_display` y `data-store="product-price-*"` son los anchors mas seguros
- `.js-product-payments-container` y `.js-free-shipping-minimum-message` pueden estilizarse, pero no conviene ocultarlos sin validar negocio y flujo

## 6. Formulario de compra

Nodo principal:

- `form#product_form.js-product-form[data-store="product-form-301455005"]`

Elementos base:

| Bloque | Etiqueta | Selector visible | Funcion |
| --- | --- | --- | --- |
| formulario | `form` | `#product_form.js-product-form[data-store="product-form-301455005"]` | compra principal |
| input hidden | `input` | `input[name="add_to_cart"]` | id base del producto |
| grid de variantes | `div` | `.js-product-variants.form-row` | agrupa opciones |
| mensaje ultima unidad | `div` | `.js-last-product` | urgencia / stock bajo |

Regla operativa:

- `data-store="product-form-*"` es el mejor anchor del form
- `.js-product-form` es util como soporte, pero sensible a comportamiento

## 7. Variantes

La estructura repite el mismo patron ya visto en quickshop, con el agregado de enlaces `href` en las opciones visibles.

### Variante color

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| grupo color | `div` | `.js-color-variants-container[data-variation-id="0"]` | scope especifico de color |
| select fallback | `select` | `#variation_1.js-variation-option` | control oculto nativo |
| label visible | `label` | `.form-label` | texto `Color:` |
| swatch | `a` | `.js-insta-variant.btn.btn-variant.btn-variant-color.selected` | chip de color |
| contenido swatch | `span` | `.btn-variant-content` | color inline |

### Variante talle

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| grupo talle | `div` | `.js-product-variants-group[data-variation-id="1"]` | scope especifico de talle |
| select fallback | `select` | `#variation_2.js-variation-option` | control oculto nativo |
| label visible | `label` | `.form-label` | texto `Talle:` |
| opcion seleccionada | `a` | `.js-insta-variant.btn.btn-variant.selected` | estado activo |
| opcion normal | `a` | `.js-insta-variant.btn.btn-variant` | estado normal |
| texto del chip | `span` | `.btn-variant-content` | label textual |

Regla operativa:

- para look visual usar `.js-product-variants-group`, `.form-label`, `.btn-variant`, `.btn-variant-color`, `.selected`
- no ocultar `select.js-variation-option` ni romper los anchors clickeables de `.js-insta-variant`

## 8. Cantidad, CTA y mensajes posteriores

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| modulo cantidad | `div` | `.js-product-quantity-container` | control de unidades | Media |
| wrapper quantity | `div` | `.form-group.js-quantity` | agrupa stepper | Media |
| stepper | `div` | `.form-quantity.form-quantity-product` | layout del control | Media |
| minus | `span` | `.js-quantity-down.form-quantity-icon.btn` | resta | Alta |
| input cantidad | `input` | `.js-quantity-input.form-control` | valor editable | Alta |
| plus | `span` | `.js-quantity-up.form-quantity-icon.btn` | suma | Alta |
| wrapper CTA | `div` | `.js-buy-button-container` | columna de compra | Media |
| boton real | `input` | `.btn-add-to-cart[data-store="product-buy-button"][data-component="product.add-to-cart"]` | CTA principal | Alta |
| stock notification | `div` | `#stock-notification-container.morelia` | modulo aviso de stock | Media |
| placeholder CTA | `div` | `.js-addtocart-placeholder` | estado cargando/listo | Alta |
| mensaje agregado | `div` | `.js-added-to-cart-product-message` | feedback post-add | Alta |
| link ver carrito | `a` | `.js-open-cart` | abre modal carrito | Media |
| promo add product | `div` | `.js-shipping-add-product-label` | incentivo shipping | Media |
| mensaje free shipping | `div` | `.js-product-form-free-shipping-message.js-free-shipping-message` | feedback shipping gratis | Media |

Regla operativa:

- el boton principal tiene anchors muy buenos: `data-store="product-buy-button"` y `data-component="product.add-to-cart"`
- no conviene eliminar `.js-addtocart-placeholder`, `.js-added-to-cart-product-message` ni los mensajes de shipping

## 9. Bloque stock notification

Este modulo parece custom, insertado dentro del bloque de compra.

| Bloque | Etiqueta | Selector visible | Observacion |
| --- | --- | --- | --- |
| contenedor | `div` | `#stock-notification-container.morelia` | scope principal |
| trigger | `div` | `#stock-notification-request-message` | CTA textual |
| dialog | `dialog` | `#stock-notification-modal-dialog.morelia` | popup interno |
| cerrar | `span` | `#stock-notification-close-button` | cierre del dialog |
| intro | `div` | `.stock-notification-intro-message` | copy introductorio |
| nombre producto | `div` | `#stock-notification-product-name` | texto dinamico |
| formulario | `form` | `#stock-notification-form` | captura email |
| email | `input` | `#stock-notification-email[type="email"]` | campo email |
| submit | `input` | `#stock-notification-submit[type="submit"]` | CTA envio |
| exito | `div` | `#stock-notification-success-message` | mensaje success |
| powered by | `div` | `.stock-notification-powered-by` | attribution |

Regla operativa:

- al tener ids dedicados, este bloque es muy controlable desde CSS
- limitarlo siempre con `#single-product` si no se quiere afectar quickshop u otras vistas

## 10. Modal de medios de pago

Nodo principal:

- `div#installments-modal.js-modal.js-fullscreen-modal.modal`

Subbloques relevantes:

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| modal raiz | `div` | `#installments-modal` | popup de medios de pago | Alta |
| header modal | `div` | `.modal-header` | titulo + cierre | Media |
| close header | `a` | `.js-modal-close.modal-close` | cerrar modal | Media |
| body scrollable | `div` | `.modal-body.modal-scrollable` | contenido principal | Media |
| contenedor tabs | `div` | `.js-tab-container` | sistema de tabs | Media |
| lista tabs | `ul` | `.js-payments-tab-group.tab-group` | navegacion de gateways | Media |
| tab | `li` | `.js-installments-gw-tab.js-tab.tab` | gateway individual | Media |
| link tab | `a` | `.js-tab-link.tab-link` | activacion visual | Media |
| descuento tab | `span` | `.js-modal-tab-discount` | badge promo | Media |
| paneles | `div` | `.js-tabs-content.tab-content` | contenido de tabs | Media |
| panel activo | `div` | `.js-tab-panel.tab-panel.js-gw-tab-pane` | un gateway especifico | Media |
| titulo metodo | `div` | `.js-payment-method-title` | nombre del metodo | Media |
| box metodo | `div` | `.js-info-payment-method-container.box` | bloque de info | Media |
| descuento metodo | `div` | `.js-payment-method-discount` | promo del metodo | Media |
| total metodo | `div` | `.js-payment-method-total` | total / cuotas | Media |
| explicacion | `div` | `.js-discount-explanation` | copy explicativa | Media |
| disclaimer | `div` | `.js-discount-disclaimer` | restricciones | Media |
| tabla cuotas | `table` | `.js-payments-table.table` | detalle de cuotas | Media |
| fila cuota | `tr` | `.js-payment-provider-installments-row` | una opcion de cuota | Media |
| total cuota | `span` | `.js-installment-total-price` | total por fila | Media |
| footer modal | `div` | `.modal-footer` | cierre secundario | Media |
| close footer | `span` | `.js-modal-close.js-fullscreen-modal-close.btn-link` | volver al producto | Media |
| overlay | `div` | `.js-modal-overlay.modal-overlay` | fondo del modal | Media |

Regla operativa:

- `#installments-modal` es el scope correcto para estilado del popup
- no conviene alterar la logica de tabs, scroll ni overlays solo con CSS estructural agresivo

## 11. Descripcion y reviews

| Bloque | Etiqueta | Selector visible | Funcion | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| descripcion | `div` | `[data-store="product-description-301455005"]` | bloque final de contenido | Alta |
| contenido usuario | `div` | `.user-content` | cuerpo editorial | Alta |
| parrafo | `p` | `p` | texto descriptivo | Baja |
| reviews app | `div` | `#reviewsapp` | mount point de reseñas | Media |

Regla operativa:

- para tipografia editorial y espaciado, usar `data-store="product-description-*"` y `.user-content`
- no depender de nodos internos de `#reviewsapp` hasta inspeccionar markup real una vez montado

## Inventario de etiquetas HTML presentes

Etiquetas confirmadas en este snapshot:

- `div`
- `section`
- `a`
- `span`
- `h1`
- `p`
- `form`
- `input`
- `label`
- `select`
- `option`
- `img`
- `svg`
- `use`
- `dialog`
- `ul`
- `li`
- `table`
- `tbody`
- `tr`
- `td`
- `small`
- `strong`

Lectura practica:

- la estructura general depende mucho de `div`, pero las zonas de negocio agregan `form`, `input`, `table`, `dialog` y `section`
- el CTA principal es `input[type="submit"]`, no `button`
- el modal de cuotas introduce una taxonomia mas rica que el resto del detalle

## Selectores recomendados para CSS

Prioridad sugerida:

1. `#single-product[data-store="product-detail"]`
2. `#single-product [data-store="product-info-301455005"]`
3. `#single-product [data-store="page-title"]`
4. `#single-product [data-store="product-name-301455005"]`
5. `#single-product [data-store="product-price-301455005"]`
6. `#price_display` y `#compare_price_display`
7. `#single-product [data-store="product-form-301455005"]`
8. `#single-product .js-product-variants-group`
9. `#single-product [data-store="product-buy-button"]`
10. `#single-product [data-store="product-description-301455005"]`
11. `#single-product #stock-notification-container`
12. `#installments-modal`

## Hooks sensibles

Conviene tratar como sensibles estos hooks:

- `.js-product-detail`
- `.js-product-container`
- `.js-shipping-calculator-container`
- `.js-swiper-product-thumbs`
- `.js-product-thumb`
- `.js-swiper-product`
- `.js-product-slide`
- `.js-product-slide-link`
- `.js-product-slide-img`
- `.js-swiper-product-prev`
- `.js-swiper-product-next`
- `.js-product-name`
- `.js-price-display`
- `.js-compare-price-display`
- `.js-product-payments-container`
- `.js-product-form`
- `.js-product-variants`
- `.js-variation-option`
- `.js-refresh-installment-data`
- `.js-insta-variant`
- `.js-quantity-down`
- `.js-quantity-up`
- `.js-quantity-input`
- `.js-addtocart`
- `.js-modal-open`
- `.js-modal-close`
- `.js-tab`
- `.js-tab-link`
- `.js-tab-panel`

Regla practica:

- se pueden usar como soporte visual cuando no haya mejor anchor
- no conviene basar la arquitectura completa en ellos si existe `data-store`, `id` o una clase visual mas estable

## Cambios visuales de bajo riesgo

- tipografia y spacing de `.page-header`, `.breadcrumbs` y `.user-content`
- estilo de `.product-thumb` y `.product-slider-image`
- apariencia de labels promocionales
- look del bloque de precio y compare price
- estilo de `.btn-variant`, `.btn-variant-color` y `.form-quantity-product`
- look del boton principal y estados visibles del placeholder
- diseño del bloque `#stock-notification-container`
- tipografia, espaciado y bordes dentro de `#installments-modal`

## Cambios con mas cuidado

- tocar wrappers `swiper-*` con cambios estructurales agresivos
- ocultar `#price_display`, `.js-product-payments-container` o mensajes de shipping
- eliminar selects fallback de variantes
- alterar la logica de tabs o scroll del modal de cuotas
- colapsar overlays o cierres del modal de medios de pago
- depender de markup interno de `#reviewsapp` sin inspeccion posterior

## Conclusiones operativas

- `#single-product[data-store="product-detail"]` es un scope muy fuerte y suficiente para casi todo el product detail.
- el detalle mezcla anchors oficiales excelentes con varios hooks `js-*` sensibles, especialmente en galeria, pricing, variantes, CTA y modal de pagos.
- para CSS durable conviene priorizar `data-store`, ids dedicados y clases visuales evidentes antes que wrappers JS.
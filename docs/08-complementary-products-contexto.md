# Contexto de complementary products

## Objetivo

Registrar la estructura HTML observada en `#complementary-products` para poder intervenirla con CSS de forma precisa, distinguiendo:

- etiquetas HTML reales
- ids, clases y atributos disponibles
- anchors mas estables para estilado
- hooks sensibles porque probablemente estan conectados a JS, Swiper o quickshop

## Alcance de este documento

Este archivo describe el `outerHTML` puntual provisto para la seccion de productos complementarios, no una garantia absoluta de todos los estados posibles de Morelia.

Lectura correcta:

1. funciona como snapshot operativo del bloque actual
2. sirve para decidir selectores en `theme.css`
3. confirma que el card reutiliza piezas del product item del grid, pero dentro de un wrapper distinto al single product

## Scope principal

Nodo raiz observado:

- `section#complementary-products.products-section.js-complementary-products.section-products-related.position-relative.mb-3[data-store="complementary-products"][data-component="complementary-products"]`

Implicancia CSS:

- `#complementary-products` es el mejor scope raiz para cualquier override local de esta seccion.
- `data-store="complementary-products"` es el anchor mas estable del bloque completo.
- `data-component="complementary-products"` sirve como apoyo si el id cambiara.
- `.js-complementary-products`, `.js-swiper-complementary`, `.js-swiper-complementary-prev` y `.js-swiper-complementary-next` deben tratarse como hooks sensibles de comportamiento.

## Diferencia operativa frente a single product

Este bloque no es parte del form principal de `#single-product`, aunque viva dentro de la pagina de detalle.

Su estructura combina dos capas:

1. un shell propio de seccion relacionada/complementaria con titulo, slider y flechas
2. un `product item` reutilizado, con imagen, labels, nombre, precio y CTA de quickshop

Conclusion CSS:

- para layout, espaciados, ancho, alineacion y navegacion, conviene arrancar por `#complementary-products`
- para tipografia e imagen del card, conviene reutilizar anchors del item (`.item-image`, `.item-description`, `.item-actions`, `.item-name`, `.item-price-container`) pero siempre scopeados dentro de `#complementary-products`
- no conviene asumir que este bloque comparte exactamente el mismo DOM que `#related-products` o que el grid de home, aunque comparta varias piezas

## Arbol estructural resumido

```text
section#complementary-products[data-store="complementary-products"]
  div.position-relative
    div.products-section-title-container.section-title.text-center
      h2.products-section-title.h5.mb-1

    div.products-section-container.swiper-container-horizontal
      div.products-section-slider-container.js-swiper-complementary.swiper-container
        div.products-section-slider-wrapper.swiper-wrapper
          div.swiper-slide.js-swiper-slide-visible.swiper-slide-active
            div.js-item-product.js-item-slide.p-0.item.item-product.grid-item[data-store="product-item-329399022"][data-component="product-list-item"]
              div.js-product-container.js-quickshop-container.js-quickshop-has-variants.position-relative[data-quickshop-id="quick329399022"]

                div.js-product-item-image-container-private.product-item-image-container.item-image[data-store="product-item-image-329399022"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_top_left"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_top_right"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_bottom_left"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_bottom_right"]
                  div.position-relative.d-block
                    a.js-product-item-image-link-private
                      img.js-product-item-image-private.product-item-image.js-item-image.img-absolute.img-absolute-centered.item-image-featured
                      div.placeholder-fade
                    div.item-floating-elements
                      div.labels.js-labels-floating-group[data-store="product-item-labels"]
                        div.js-stock-label-private[data-store="product-item-label-stock"]
                        div.js-offer-label-private[data-store="product-item-offer-label"]
                          span.label-offer-percentage
                          span.label-offer-percentage-text
                        div.js-shipping-label-private.js-free-shipping-minimum-label[data-store="product-item-label-shipping"]
                      span.hidden[data-store="stock-product-329399022-3"]
                      span.js-free-shipping-combines-config.hidden

                div.js-item-variants.hidden
                  form.js-product-form[action="/comprar/"]
                    input[type="hidden"][name="add_to_cart"]
                    div.js-product-variants.js-product-quickshop-variants.mb-3.form-row
                      div.js-product-variants-group.js-color-variants-container[data-variation-id="0"]
                        div.form-group.mb-2.d-none
                          label.form-label
                          select#variation_1.js-variation-option.js-refresh-installment-data.form-select
                          div.form-select-icon
                            svg
                        div.row
                          div.col-auto
                            label.form-label.d-inline-block.mt-2
                          div.col.pl-0
                            a.js-insta-variant.btn.btn-variant.selected.btn-variant-color
                              span.btn-variant-content

                      div.js-product-variants-group[data-variation-id="1"]
                        div.form-group.mb-2.d-none
                          label.form-label
                          select#variation_2.js-variation-option.js-refresh-installment-data.form-select
                          div.form-select-icon
                            svg
                        div.row
                          div.col-auto
                            label.form-label.d-inline-block.mt-2
                          div.col.pl-0
                            a.js-insta-variant.btn.btn-variant
                              span.btn-variant-content

                    input.js-addtocart.js-prod-submit-form.btn.btn-primary.w-100.mb-2.cart[type="submit"]
                    div.js-addtocart.js-addtocart-placeholder.btn.btn-primary.btn-block.btn-transition.mb-2.disabled

                div.js-item-description.item-description[data-store="product-item-info-329399022"]
                  a.item-link
                    div.js-item-name.item-name.mb-2[data-store="product-item-name-329399022"]
                    div.js-item-price-container.item-price-container.mb-2[data-store="product-item-price-329399022"]
                      span.js-compare-price-display.price-compare
                      span.js-price-display.item-price
                  div.js-item-quickshop.item-actions.mt-3
                    a.js-quickshop-modal-open.js-quickshop-slide.js-modal-open.js-fullscreen-modal-open.btn.btn-primary.btn-small[data-component="product-list-item.add-to-cart"]

              script[type="application/ld+json"][data-component="structured-data.item"]

      div.products-section-prev-container.js-swiper-complementary-prev.swiper-button-prev
        svg.products-section-slider-control.products-section-slider-control-prev
          use

      div.products-section-next-container.js-swiper-complementary-next.swiper-button-next
        svg.products-section-slider-control.products-section-slider-control-next
          use
```

## Mapa por bloques

## 1. Contenedor raiz y encabezado

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| raiz de seccion | `section` | `#complementary-products[data-store="complementary-products"]` | scope principal del modulo | Alta |
| wrapper interno | `div` | `.position-relative` | contiene titulo, slider y flechas | Baja |
| contenedor titulo | `div` | `.products-section-title-container.section-title.text-center` | header del modulo | Media |
| titulo | `h2` | `.products-section-title.h5` | heading visible | Media |

Regla operativa:

- para separar visualmente la seccion del resto del product detail, arrancar por `#complementary-products`
- para tipografia, tracking y espaciado del titulo, usar `.products-section-title` scopeado por la seccion

## 2. Shell del slider

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| contenedor del carrusel | `div` | `.products-section-container` | marco general del slider | Media |
| swiper principal | `div` | `.products-section-slider-container.js-swiper-complementary.swiper-container` | inicializa el slider | Media |
| wrapper de slides | `div` | `.products-section-slider-wrapper.swiper-wrapper` | track horizontal | Media |
| slide | `div` | `.swiper-slide` | card individual dentro del carrusel | Media |

Notas:

- aunque en el snapshot solo haya un producto, el modulo esta montado como carrusel.
- `swiper-slide-active`, `swiper-button-disabled` y `swiper-button-lock` son estados runtime, no anchors de larga vida.
- si se trabaja ancho de card, gutters o centrado, conviene tocar el shell del slider antes que los estados runtime de Swiper.

## 3. Card de producto reutilizado

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| item root | `div` | `.item.item-product.grid-item[data-store^="product-item-"]` | card del producto | Alta |
| contenedor funcional | `div` | `.js-product-container.js-quickshop-container.position-relative` | shell de quickshop/list item | Media |
| descripcion completa | `div` | `.item-description[data-store^="product-item-info-"]` | nombre, precio y CTA | Alta |
| acciones | `div` | `.item-actions` | CTA visible del card | Alta |

Regla operativa:

- esta capa coincide bastante con la taxonomia del product item en home y listados.
- para CSS durable, conviene priorizar `.item-product`, `.item-image`, `.item-description`, `.item-name`, `.item-price-container`, `.item-actions` y `data-store="product-item-*"`.
- `.js-item-slide`, `.js-item-product` y `.js-product-container` son utiles solo como contexto secundario.

## 4. Bloque de imagen y labels

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| wrapper imagen | `div` | `.product-item-image-container.item-image[data-store^="product-item-image-"]` | caja visual de la imagen | Alta |
| link imagen | `a` | `.js-product-item-image-link-private` | link al PDP | Baja |
| imagen | `img` | `.product-item-image.js-item-image.item-image-featured` | imagen principal del card | Media |
| floating elements | `div` | `.item-floating-elements` | overlay de labels | Media |
| grupo labels | `div` | `.labels[data-store="product-item-labels"]` | stock, promo y shipping | Alta |
| label shipping | `div` | `.js-free-shipping-minimum-label[data-store="product-item-label-shipping"]` | badge visible en snapshot | Alta |

Notas:

- los `div.js-nubesdk-slot` son slots de apps; no conviene construir layout critico apoyado en ellos.
- el badge de envio gratis vive dentro del overlay de imagen, no en la descripcion del card.
- `placeholder-fade`, `lazyloaded`, `ls-is-cached` y `lazyautosizes` responden a lazy loading; no son buenos anchors base.

## 5. Variantes y compra interna ocultas

Bloque observado:

- `div.js-item-variants.hidden`

Contenido confirmado:

- `form.js-product-form`
- `input[name="add_to_cart"]`
- `div.js-product-variants.js-product-quickshop-variants`
- grupos por variacion con `data-variation-id`
- botones `.js-insta-variant.btn.btn-variant`
- submit `input.js-addtocart.js-prod-submit-form`
- placeholder `.js-addtocart.js-addtocart-placeholder`

Lectura operativa:

- este producto complementario ya trae dentro del card un mini form de compra/variantes, pero en el snapshot esta oculto por `.hidden`.
- el CTA visible del usuario no es ese submit, sino el link de quickshop dentro de `.item-actions`.
- si en otro estado Tienda Nube expusiera este bloque, los hooks de variantes y add to cart ya estan montados y no deberian romperse con overrides agresivos.

Regla CSS:

- evitar reglas globales sobre `.js-item-variants`, `.js-product-form`, `.js-insta-variant` o `.js-addtocart` sin scope fuerte, porque estas clases se repiten en quickshop y product detail.

## 6. Nombre y precio

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| wrapper info | `div` | `.item-description[data-store^="product-item-info-"]` | cuerpo textual del card | Alta |
| link textual | `a` | `.item-link` | link al producto | Media |
| nombre | `div` | `.item-name[data-store^="product-item-name-"]` | titulo visible | Alta |
| contenedor precio | `div` | `.item-price-container[data-store^="product-item-price-"]` | wrapper de precios | Alta |
| compare price | `span` | `.js-compare-price-display.price-compare` | promo/tachado | Media |
| precio actual | `span` | `.js-price-display.item-price` | precio visible | Alta |

Regla operativa:

- para jerarquia tipografica, pesos, interlineado y espaciados, la mejor entrada es `.item-description` con sus subbloques.
- para estilos persistentes del valor monetario, conviene priorizar `.item-price` y `data-store^="product-item-price-"`.

## 7. CTA visible

Bloque observado:

- `div.js-item-quickshop.item-actions.mt-3`
- `a.js-quickshop-modal-open.js-quickshop-slide.js-modal-open.js-fullscreen-modal-open.btn.btn-primary.btn-small[data-component="product-list-item.add-to-cart"]`

Lectura operativa:

- el boton visible del snapshot es un link que abre quickshop, no un `button` ni un `input[type="submit"]`.
- esto explica por que el card se comporta distinto al formulario del single product.

Regla CSS:

- para estilado durable del CTA visible, conviene usar `#complementary-products .item-actions .btn` o `#complementary-products [data-component="product-list-item.add-to-cart"]`.
- no conviene apuntar solo a `.js-quickshop-modal-open`, porque ese hook existe tambien en otros contextos.

## 8. Controles laterales del slider

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| prev wrapper | `div` | `.products-section-prev-container.swiper-button-prev` | control anterior | Media |
| next wrapper | `div` | `.products-section-next-container.swiper-button-next` | control siguiente | Media |
| iconos | `svg` | `.products-section-slider-control-prev` / `.products-section-slider-control-next` | flechas visuales | Media |

Notas:

- en el snapshot ambos controles aparecen bloqueados por `swiper-button-disabled` y `swiper-button-lock`.
- la clase `d-none d-md-block` confirma que las flechas laterales estan pensadas para desktop.

## 9. Structured data y metadata interna

Bloque observado:

- `script[type="application/ld+json"][data-component="structured-data.item"]`

Lectura operativa:

- este nodo no sirve para CSS.
- confirma que cada slide puede incluir metadata SEO del producto renderizado.

## Tags HTML confirmados en este snapshot

Etiquetas vistas directamente en el fragmento:

- `section`
- `div`
- `h2`
- `a`
- `img`
- `span`
- `form`
- `input`
- `label`
- `select`
- `option`
- `svg`
- `use`
- `script`

## Anchors recomendados para futuros overrides

### Nivel seccion

- `#complementary-products`
- `[data-store="complementary-products"]`
- `[data-component="complementary-products"]`
- `.products-section-title`
- `.products-section-container`
- `.products-section-slider-container`

### Nivel card

- `.item-product`
- `.item-image`
- `.product-item-image-container`
- `.item-description`
- `.item-name`
- `.item-price-container`
- `.item-price`
- `.item-actions`
- `[data-store^="product-item-"]`
- `[data-store^="product-item-image-"]`
- `[data-store^="product-item-info-"]`
- `[data-store^="product-item-name-"]`
- `[data-store^="product-item-price-"]`

### Nivel CTA y labels

- `[data-component="product-list-item.add-to-cart"]`
- `[data-store="product-item-labels"]`
- `[data-store="product-item-label-shipping"]`

## Hooks sensibles o de baja prioridad para CSS durable

- `.js-complementary-products`
- `.js-swiper-complementary`
- `.js-swiper-complementary-prev`
- `.js-swiper-complementary-next`
- `.js-item-product`
- `.js-item-slide`
- `.js-product-container`
- `.js-quickshop-container`
- `.js-product-item-image-link-private`
- `.js-product-item-image-private`
- `.js-item-variants`
- `.js-product-form`
- `.js-variation-option`
- `.js-insta-variant`
- `.js-addtocart`
- `.js-quickshop-modal-open`
- `.js-modal-open`

Motivo:

- casi todos estos hooks parecen estar ligados a interacciones, hydration, quickshop o slider.
- pueden servir como contexto auxiliar, pero no deberian ser la primera opcion para selectores de larga vida.

## Conclusiones operativas para la futura capa CSS

1. El scope correcto para intervenir este modulo es `#complementary-products`, no `#single-product` a secas.
2. El card interno reutiliza la taxonomia del product item, por lo que conviene trabajar sobre `.item-*` y `data-store="product-item-*"` dentro del scope complementario.
3. El CTA visible es un link de quickshop, no el submit oculto del formulario interno.
4. El badge de envio gratis vive en el overlay de imagen, asi que cualquier cambio de layout debe considerar esa superposicion.
5. El shell del slider y sus flechas tienen estructura propia; no conviene tratarlos como si fueran la grilla comun de listados.
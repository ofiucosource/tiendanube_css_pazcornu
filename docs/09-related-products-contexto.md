# Contexto de related products

## Objetivo

Registrar la estructura HTML observada en `#related-products` para poder intervenirla con CSS de forma precisa, distinguiendo:

- etiquetas HTML reales
- ids, clases y atributos disponibles
- anchors mas estables para estilado
- hooks sensibles porque probablemente estan conectados a JS, Swiper o quickshop
- diferencias reales frente a `#complementary-products` para futuras unificaciones de card

## Alcance de este documento

Este archivo describe el `outerHTML` puntual provisto para la seccion de productos relacionados, no una garantia absoluta de todos los estados posibles de Morelia.

Lectura correcta:

1. funciona como snapshot operativo del bloque actual
2. sirve para decidir selectores en `theme.css`
3. confirma que el modulo reutiliza el `product item`, pero con estados adicionales que no aparecian en complementary

## Scope principal

Nodo raiz observado:

- `section#related-products.products-section.js-related-products.section-products-related.position-relative.mb-3[data-store="related-products"][data-component="related-products"]`

Implicancia CSS:

- `#related-products` es el mejor scope raiz para cualquier override local de esta seccion.
- `data-store="related-products"` es el anchor mas estable del bloque completo.
- `data-component="related-products"` sirve como apoyo si el id cambiara.
- `.js-related-products`, `.js-swiper-related`, `.js-swiper-related-prev` y `.js-swiper-related-next` deben tratarse como hooks sensibles de comportamiento.

## Relacion operativa con complementary products

La seccion comparte el mismo shell general que `#complementary-products`:

1. heading del modulo
2. slider horizontal con wrappers Swiper
3. cards que reutilizan el markup del `product item`

Pero en este snapshot aparecen diferencias concretas que importan para CSS:

- hay muchas mas slides y Swiper duplica nodos con `.swiper-slide-duplicate`
- aparecen cards con imagen secundaria real y estados `product-item-secondary-images-loaded`
- aparecen precios promocionales visibles con `.price-compare`
- aparecen labels de descuento activas con porcentaje OFF visible
- conviven labels de envio gratis visibles y ocultas segun producto

Conclusion CSS:

- el layout del modulo puede unificarse con complementary, pero el card necesita contemplar mas estados de imagen y pricing.
- cualquier unificacion debe partir de anchors compartidos del `product item`, no de estados runtime de Swiper.

## Arbol estructural resumido

```text
section#related-products[data-store="related-products"]
  div.position-relative
    div.products-section-title-container.section-title.text-center
      h2.products-section-title.h5.mb-1

    div.products-section-container.swiper-container-horizontal
      div.products-section-slider-container.js-swiper-related.swiper-container
        div.products-section-slider-wrapper.swiper-wrapper
          div.swiper-slide
            div.js-item-product.js-item-slide.p-0.item.item-product.grid-item[data-store="product-item-182212619"][data-component="product-list-item"]
              div.js-product-container.js-quickshop-container.js-quickshop-has-variants.position-relative[data-quickshop-id="quick182212619"]

                div.js-product-item-image-container-private.product-item-image-container.item-image[data-store="product-item-image-182212619"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_top_left"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_top_right"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_bottom_left"]
                  div.js-nubesdk-slot[data-nubesdk-slot="product_grid_item_image_bottom_right"]
                  div.position-relative.d-block
                    a.js-product-item-image-link-private
                      img.js-product-item-image-private.product-item-image.js-item-image.product-item-image-featured.item-image-featured
                      img.js-product-item-image-private.product-item-image.js-item-image.js-product-item-secondary-image-private.product-item-image-secondary.item-image-secondary
                      div.placeholder-fade
                    div.item-floating-elements
                      div.labels.js-labels-floating-group[data-store="product-item-labels"]
                        div.js-stock-label-private[data-store="product-item-label-stock"]
                        div.js-offer-label-private[data-store="product-item-offer-label"]
                          span.label-offer-percentage
                          span.label-offer-percentage-text
                        div.js-shipping-label-private.js-free-shipping-minimum-label[data-store="product-item-label-shipping"]
                      span.hidden[data-store^="stock-product-"]
                      span.js-free-shipping-combines-config.hidden

                div.js-item-variants.hidden
                  form.js-product-form[action="/comprar/"]
                    input[type="hidden"][name="add_to_cart"]
                    div.js-product-variants.js-product-quickshop-variants.mb-3.form-row.pt-2
                      div.js-product-variants-group.js-color-variants-container[data-variation-id="0"]
                      div.js-product-variants-group[data-variation-id="1"]
                    input.js-addtocart.js-prod-submit-form.btn.btn-primary.w-100.mb-2.cart[type="submit"]
                    div.js-addtocart.js-addtocart-placeholder.btn.btn-primary.btn-block.btn-transition.mb-2.disabled

                div.js-item-description.item-description[data-store="product-item-info-182212619"]
                  a.item-link
                    div.js-item-name.item-name.mb-2[data-store="product-item-name-182212619"]
                    div.js-item-price-container.item-price-container.mb-2[data-store="product-item-price-182212619"]
                      span.js-compare-price-display.price-compare
                      span.js-price-display.item-price
                  div.js-item-quickshop.item-actions.mt-3
                    a.js-quickshop-modal-open.js-quickshop-slide.js-modal-open.js-fullscreen-modal-open.btn.btn-primary.btn-small[data-component="product-list-item.add-to-cart"]

              script[type="application/ld+json"][data-component="structured-data.item"]

      div.products-section-prev-container.js-swiper-related-prev.swiper-button-prev
        svg.products-section-slider-control.products-section-slider-control-prev
          use

      div.products-section-next-container.js-swiper-related-next.swiper-button-next
        svg.products-section-slider-control.products-section-slider-control-next
          use
```

## Mapa por bloques

## 1. Contenedor raiz y encabezado

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| raiz de seccion | `section` | `#related-products[data-store="related-products"]` | scope principal del modulo | Alta |
| wrapper interno | `div` | `.position-relative` | contiene titulo, slider y flechas | Baja |
| contenedor titulo | `div` | `.products-section-title-container.section-title.text-center` | header del modulo | Media |
| titulo | `h2` | `.products-section-title.h5` | heading visible | Media |

Regla operativa:

- para espaciado, separacion y ancho del modulo, arrancar por `#related-products`
- para tratamiento del titulo, usar `.products-section-title` scopeado al modulo

## 2. Shell del slider y estados Swiper

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| contenedor del carrusel | `div` | `.products-section-container` | marco general del slider | Media |
| swiper principal | `div` | `.products-section-slider-container.js-swiper-related.swiper-container` | inicializa el slider | Media |
| wrapper de slides | `div` | `.products-section-slider-wrapper.swiper-wrapper` | track horizontal | Media |
| slide | `div` | `.swiper-slide` | card individual dentro del carrusel | Media |
| slide duplicada | `div` | `.swiper-slide-duplicate` | clon runtime de Swiper | Baja |

Notas:

- a diferencia de complementary, aca el snapshot confirma clones activos de Swiper.
- tambien aparecen estados runtime como `.swiper-slide-active`, `.swiper-slide-next`, `.swiper-slide-prev`, `.swiper-slide-duplicate-active` y `.swiper-slide-duplicate-next`.
- estos estados sirven para debug o microajustes muy puntuales, pero no deberian ser la base de una unificacion durable.

## 3. Card de producto reutilizado

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| item root | `div` | `.item.item-product.grid-item[data-store^="product-item-"]` | card del producto | Alta |
| contenedor funcional | `div` | `.js-product-container.js-quickshop-container.position-relative` | shell de quickshop/list item | Media |
| descripcion completa | `div` | `.item-description[data-store^="product-item-info-"]` | nombre, precio y CTA | Alta |
| acciones | `div` | `.item-actions` | CTA visible del card | Alta |

Regla operativa:

- esta capa es compatible con la misma estrategia usada para complementary.
- para una futura unificacion de cards, conviene abrir reglas compartidas sobre `.item-product`, `.item-image`, `.item-description`, `.item-name`, `.item-price-container`, `.item-price` y `.item-actions`, scopeadas por `#related-products, #complementary-products`.

## 4. Imagen principal, imagen secundaria y estados de hover

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| wrapper imagen | `div` | `.product-item-image-container.item-image[data-store^="product-item-image-"]` | caja visual de imagen | Alta |
| wrapper con secundarias | `div` | `.js-product-item-private-with-secondary-images` | indica segunda imagen disponible | Baja |
| wrapper cargado | `div` | `.product-item-secondary-images-loaded` | estado runtime de carga | Baja |
| imagen featured | `img` | `.product-item-image-featured.item-image-featured` | imagen principal | Media |
| imagen secundaria | `img` | `.product-item-image-secondary.item-image-secondary` | segunda imagen del card | Media |

Notas:

- esta es la diferencia estructural mas relevante frente a complementary.
- algunos productos muestran segunda imagen ya cargada y visible en DOM.
- si se va a unificar la experiencia visual de cards, hay que decidir si el hover con segunda imagen queda activo en ambas secciones o se desactiva en ambas.

Regla CSS:

- para overflow, proporciones y recorte, usar `.product-item-image-container`.
- para cualquier tratamiento del hover de imagen, conviene trabajar sobre `.product-item-image-featured` y `.product-item-image-secondary` dentro del scope de la seccion.
- no conviene basar reglas estructurales en `.product-item-secondary-images-loaded`, porque es un estado mutable.

## 5. Labels y estados promocionales

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| grupo labels | `div` | `.labels[data-store="product-item-labels"]` | wrapper de badges | Alta |
| stock label | `div` | `[data-store="product-item-label-stock"]` | sin stock | Alta |
| offer label | `div` | `[data-store="product-item-offer-label"]` | promo OFF | Alta |
| offer percentage | `span` | `.label-offer-percentage` | porcentaje visual | Media |
| shipping label | `div` | `[data-store="product-item-label-shipping"]` | envio gratis | Alta |

Notas:

- en related aparecen mas estados activos que en complementary: descuentos visibles, compare price visible y shipping a veces oculto.
- esto hace que la altura y densidad visual de la card varien mas entre productos.

Regla operativa:

- si se busca unificar cards, conviene estabilizar primero el area de labels y el bloque de precio antes de tocar el CTA.

## 6. Variantes y compra interna ocultas

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

- igual que en complementary, el card ya trae el mini form interno pero oculto por `.hidden`.
- el CTA visible sigue siendo el link de quickshop dentro de `.item-actions`.
- como hay muchos productos y combinaciones, este bloque confirma que related comparte la misma base funcional del product item de listados.

## 7. Nombre, precio actual y compare price

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| wrapper info | `div` | `.item-description[data-store^="product-item-info-"]` | cuerpo textual del card | Alta |
| nombre | `div` | `.item-name[data-store^="product-item-name-"]` | titulo visible | Alta |
| contenedor precio | `div` | `.item-price-container[data-store^="product-item-price-"]` | wrapper de precios | Alta |
| compare price | `span` | `.js-compare-price-display.price-compare` | precio tachado/promocional | Media |
| precio actual | `span` | `.js-price-display.item-price` | precio vigente | Alta |

Notas:

- en este snapshot hay cards con `price-compare` visible y otras con el compare oculto.
- esto introduce una altura variable que no estaba tan marcada en complementary.

Regla CSS:

- para una unificacion robusta, conviene normalizar el bloque `.item-price-container` como una zona de dos lineas posibles.
- si se quiere evitar saltos de layout, hay que contemplar el caso con y sin compare price.

## 8. CTA visible

Bloque observado:

- `div.js-item-quickshop.item-actions.mt-3`
- `a.js-quickshop-modal-open.js-quickshop-slide.js-modal-open.js-fullscreen-modal-open.btn.btn-primary.btn-small[data-component="product-list-item.add-to-cart"]`

Lectura operativa:

- igual que en complementary, el CTA visible es un link de quickshop, no un submit del form interno.
- por lo tanto, la unificacion de cards puede compartir la misma estrategia de boton visible entre ambos modulos.

## 9. Controles laterales del slider

| Bloque | Etiqueta | Selector visible | Funcion aparente | Estabilidad CSS |
| --- | --- | --- | --- | --- |
| prev wrapper | `div` | `.products-section-prev-container.swiper-button-prev` | control anterior | Media |
| next wrapper | `div` | `.products-section-next-container.swiper-button-next` | control siguiente | Media |
| iconos | `svg` | `.products-section-slider-control-prev` / `.products-section-slider-control-next` | flechas visuales | Media |

Notas:

- a diferencia del snapshot de complementary, aca las flechas aparecen activas y sin estado `swiper-button-lock`.
- esto sugiere que related debe testearse con mas de un viewport y con desplazamiento real del carrusel.

## 10. Structured data y metadata interna

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

- `#related-products`
- `[data-store="related-products"]`
- `[data-component="related-products"]`
- `.products-section-title`
- `.products-section-container`
- `.products-section-slider-container`

### Nivel card compartible con complementary

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

### Nivel promociones e imagen secundaria

- `[data-store="product-item-offer-label"]`
- `[data-store="product-item-label-shipping"]`
- `.price-compare`
- `.product-item-image-featured`
- `.product-item-image-secondary`

## Hooks sensibles o de baja prioridad para CSS durable

- `.js-related-products`
- `.js-swiper-related`
- `.js-swiper-related-prev`
- `.js-swiper-related-next`
- `.swiper-slide-duplicate`
- `.swiper-slide-active`
- `.swiper-slide-prev`
- `.swiper-slide-next`
- `.js-item-product`
- `.js-item-slide`
- `.js-product-container`
- `.js-quickshop-container`
- `.js-product-item-private-with-secondary-images`
- `.product-item-secondary-images-loaded`
- `.js-item-variants`
- `.js-product-form`
- `.js-insta-variant`
- `.js-addtocart`
- `.js-quickshop-modal-open`

Motivo:

- casi todos estos hooks parecen estar ligados a interacciones, runtime states, slider o quickshop.
- pueden usarse como contexto auxiliar, pero no deberian ser la primera opcion para una capa CSS estable.

## Conclusiones operativas para la futura unificacion

1. El scope correcto del modulo es `#related-products`, no una regla global sobre `section-products-related` sin contexto.
2. Related y complementary comparten el esqueleto del card, asi que la unificacion debe apoyarse en `.item-*` y `data-store="product-item-*"`.
3. Related introduce estados que la unificacion tiene que cubrir: imagen secundaria, compare price visible y labels de descuento activos.
4. El CTA visible sigue siendo el link de quickshop, por lo que el boton puede resolverse con la misma estrategia que complementary.
5. Si se busca consistencia visual real entre ambas secciones, primero hay que decidir como se van a resolver dos variaciones: cards con promo y cards con doble imagen.
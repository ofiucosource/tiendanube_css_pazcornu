# Documentacion de referencia

Este directorio resume el contexto oficial necesario para trabajar el CSS personalizado de una tienda Tienda Nube con template Morelia sin romper componentes sensibles.

Archivos incluidos:

- 01-tiendanube-morelia-contexto.md: marco tecnico general de Tienda Nube, Morelia y el theme Base como referencia.
- 02-mapa-selectores-theme-actual.md: traduccion de los selectores usados en theme.css a componentes y hooks documentados.
- 03-direccion-visual-zara.md: lineamientos esteticos para futuras iteraciones, inspirados en Zara pero aterrizados al proyecto actual.
- 04-guidelines-diseno-editorial.md: sistema de criterios visuales y de interaccion para mantener consistencia en navbar, dropdowns, producto y grilla.
- 05-taxonomia-html-tiendanube-morelia.md: mapa de etiquetas HTML, bloques por template y anchors oficiales para CSS preciso en Tiendanube, con foco operativo en Morelia.
- 06-quickshop-modal-contexto.md: snapshot operativo del DOM de `#quickshop-modal`, con etiquetas, ids, clases, anchors CSS y hooks sensibles.
- 07-single-product-contexto.md: snapshot operativo del DOM de `#single-product`, con galeria, precio, formulario, cuotas, descripcion y modal de pagos.

Nota importante:

- Despues de la unificacion de listados, `02-mapa-selectores-theme-actual.md` tambien documenta scopes validados en preview para category, subcategory, collection, search, filtros y paginacion. Ese archivo debe ser la primera referencia antes de abrir nuevos selectores.

Uso recomendado:

1. Leer primero 01-tiendanube-morelia-contexto.md.
2. Leer 05-taxonomia-html-tiendanube-morelia.md si el cambio depende de entender bloques, templates o etiquetas del DOM.
3. Leer 06-quickshop-modal-contexto.md si el cambio afecta quickshop, variantes, cantidad, CTA o stock notification dentro del modal.
4. Leer 07-single-product-contexto.md si el cambio afecta product detail, galeria, precio, variantes, CTA, descripcion o modal de medios de pago.
5. Validar cualquier cambio contra 02-mapa-selectores-theme-actual.md.
6. Usar 04-guidelines-diseno-editorial.md para mantener coherencia visual y evitar abrir caminos no validados.
7. Usar 03-direccion-visual-zara.md para decidir tono visual y prioridades de refinamiento.

Conclusion operativa:

- Morelia es una plantilla nativa de Tienda Nube.
- Morelia corre sobre grilla y utilities de Bootstrap 4.
- Gran parte de los hooks usados en el CSS actual coinciden con los componentes documentados en Snipplets, Product, Payments, Shipping, Home y Page Header.
- Los hooks con prefijo js- son sensibles porque suelen estar atados a comportamiento JS.
- Los atributos data-store son los anchors mas seguros para CSS de larga vida.
- La documentacion oficial no publica un inventario cerrado de todo el DOM de Morelia, por lo que la referencia correcta es taxonomia oficial de templates + snipplets + `data-store` + inspeccion del DOM real.
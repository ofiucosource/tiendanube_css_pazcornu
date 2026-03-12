# Documentacion de referencia

Este directorio resume el contexto oficial necesario para trabajar el CSS personalizado de una tienda Tienda Nube con template Morelia sin romper componentes sensibles.

Archivos incluidos:

- 01-tiendanube-morelia-contexto.md: marco tecnico general de Tienda Nube, Morelia y el theme Base como referencia.
- 02-mapa-selectores-theme-actual.md: traduccion de los selectores usados en theme.css a componentes y hooks documentados.
- 03-direccion-visual-zara.md: lineamientos esteticos para futuras iteraciones, inspirados en Zara pero aterrizados al proyecto actual.

Uso recomendado:

1. Leer primero 01-tiendanube-morelia-contexto.md.
2. Validar cualquier cambio contra 02-mapa-selectores-theme-actual.md.
3. Usar 03-direccion-visual-zara.md para decidir tono visual y prioridades de refinamiento.

Conclusion operativa:

- Morelia es una plantilla nativa de Tienda Nube.
- Morelia corre sobre grilla y utilities de Bootstrap 4.
- Gran parte de los hooks usados en el CSS actual coinciden con los componentes documentados en Snipplets, Product, Payments, Shipping, Home y Page Header.
- Los hooks con prefijo js- son sensibles porque suelen estar atados a comportamiento JS.
- Los atributos data-store son los anchors mas seguros para CSS de larga vida.
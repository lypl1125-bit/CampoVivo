# a. Manual De Usuario

Plataforma integral de gestión agroecológica, telemetría IoT, contabilidad, comercio orgánico e inversión rural para granjas de Santander.

## A. Propósito Del Sistema

CampoVivo es una aplicación web diseñada para apoyar la operación y proyección financiera de granjas agroecológicas en Santander, centralizando los procesos clave de productores, compradores y aportantes de capital.

* **Acceso multi-rol:** autentificación diferenciada para los perfiles Agricultor, Cliente e Inversionista.
* **Georreferenciación de predios:** captura de coordenadas GPS mediante el navegador o selección directa sobre mapa interactivo (municipios y veredas de Santander).
* **Monitoreo ambiental y simulación IoT:** visualización de variables ambientales y simulación de nodos ESP32 con respaldo offline-first (SD Local).
* **Gestión administrativa y contable:** control de ingresos, egresos y nómina, junto con inventario y alertas de stock mínimo.
* **Comercio electrónico orgánico:** catálogo de productos agrícolas, aplicación de cupones promocionales y emisión de factura digital imprimible.
* **Portal de inversión:** métricas financieras de referencia, proyección a 5 años y simulación de aportes por granja.

## B. Acceso y registro de usuarios

El ingreso al sistema y la configuración inicial de cuenta se realizan desde la vista principal de la plataforma:

1. **Abrir la aplicación:** ingresa a la URL pública de CampoVivo desde tu navegador web.
2. **Iniciar sesión o crear cuenta:**
   * **a. Iniciar sesión:** elige tu rol (Agricultor, Cliente o Inversionista), digita tu correo y contraseña, o utiliza los botones de Acceso rápido para demo (un clic) para ingresar de inmediato con datos de prueba.
   * **b. Registrarse:** selecciona la pestaña Registrarse, define tu rol y completa los datos básicos solicitados.
3. **Completar datos de la granja (rol Agricultor):** si te registras como Agricultor, registra la información de tu predio en Santander:
   * **a.** Nombre de la granja, municipio, extensión/área, cultivo principal y meta de inversión.
   * **b. Ubicación GPS (`POINT(lat lon)`):** obtén la posición con GPS en vivo, abre Elegir en mapa para buscar un municipio o vereda de Santander, haz clic o arrastra el marcador, o escribe el municipio para centrar la vista automáticamente.
   * **c. Producto inicial (opcional):** registra un primer producto para habilitarlo en la tienda.
4. **Acciones de la barra superior:** desde el encabezado tienes acceso rápido a Ir a Tienda Pública, Cerrar sesión y Restaurar Demo (restablece los datos de demostración a su estado inicial).

## C. Panel del Agricultor

Al iniciar sesión con el perfil Agricultor, el menú lateral organiza la operación diaria en tres módulos operativos y el acceso al portal de inversionistas.

### 1) Tablero IoT y Simulador MQTT

1. **Indicadores principales y gráfica horaria:** consulta la temperatura promedio, humedad promedio, cantidad de sensores activos y lecturas registradas en el día, acompañadas de la gráfica de evolución de las últimas horas.
2. **Alertas y estado de nodos:** ante una anomalía o desconexión en un sensor, se muestra un aviso superior junto con el estado de cada nodo (ESP32-01 a ESP32-05). Desde el panel puedes normalizar lecturas o reconectar nodos y comprobar que la alerta desaparezca al resolverse el evento.
3. **Simulador Broker MQTT & Nodos ESP32:**
   * **a.** Selecciona el nodo, ajusta los valores de humedad y temperatura y presiona Transmitir JSON (o emplea + Simular Trama ESP32 y Probar Trama Corrupta para verificar el rechazo de paquetes no válidos).
   * **b.** Activa Cortar Red para simular interrupciones de conectividad rural: las lecturas válidas quedan almacenadas en SD Local y se sincronizan automáticamente al pulsar Restaurar Red.

### 2) Contabilidad

1. **Resumen financiero:** revisa Ingresos acumulados, Egresos y nómina y Balance neto actual.
2. **Registro de movimientos:** en Registrar movimiento, selecciona el tipo (Ingreso, Egreso o Nómina), redacta el concepto, indica el valor en COP y la fecha, y guarda para actualizar el balance general.
3. **Exportación:** utiliza Exportar Reporte PDF para imprimir o guardar el informe desde el navegador.

### 3) Inventario

1. **Alta de ítems:** registra nuevos lotes o insumos especificando nombre, categoría, unidad de medida, stock actual, stock mínimo, precio unitario y si se publica en la tienda.
2. **Ajuste rápido y alertas:** modifica cantidades con los controles − y +5. Los registros cuyo stock sea igual o inferior al mínimo definido aparecen destacados como Stock crítico.

## D. Tienda en Línea y Factura Digital

El flujo de compra en línea permite adquirir productos orgánicos y obtener el comprobante correspondiente:

1. Accede a Tienda (o inicia sesión como Cliente).
2. Filtra el catálogo por categoría (Todos, Hortalizas, Frutas, Café, Granja) o por Granja.
3. Añade artículos al carrito con +, ajusta las cantidades con − y +, o limpia la selección con Vaciar.
4. Si dispones de un código promocional, ingrésalo en el campo de cupón (por ejemplo, `DESCUENTO202610` para un 10 % de descuento) y haz clic en Aplicar.
5. Completa los datos de entrega y selecciona Finalizar compra y generar factura.
6. El sistema descontará las unidades del inventario, registrará el ingreso correspondiente y desplegará la Factura Digital, lista para usar Imprimir / Guardar PDF.

## E. Portal de Inversionistas

El módulo de inversión ofrece información financiera y herramientas de simulación para evaluar oportunidades en las granjas registradas:

1. Ingresa a Granjas e Inversión (o inicia sesión con el rol Inversionista).
2. Consulta los indicadores generales: Inversión inicial CAPEX, VPN proyectado a 5 años, TIR estimada y Mi portafolio activo.
3. Revisa el Catálogo de granjas disponibles para inversión, donde se detallan municipio, área, cultivo, eficiencia IoT, ROI estimado y porcentaje de financiación alcanzado.
4. Digita el monto a aportar en COP (desde un mínimo de `$500.000`) sobre la granja seleccionada y pulsa Invertir para simular la operación, actualizar el avance financiado y visualizar la Proyección de flujo de fondos (5 años).
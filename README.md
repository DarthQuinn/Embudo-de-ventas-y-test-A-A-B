# Embudo-de-ventas-y-test-A-A-B

🚀 Sobre Este Proyecto
"Los datos hablan, pero hay que saber escucharlos con rigor."
Este proyecto demuestra competencias clave para roles de Data Analyst y Product Analyst:

✅ Pensamiento crítico: Cuestionar la validez de los datos antes de sacar conclusiones

✅ Rigor estadístico: No conformarse con p-values "casi significativos" — aplicar correcciones de Bonferroni

✅ Diseño experimental: Uso de controles duplicados (A/A) para detectar sesgos

✅ Orientación a negocio: Traducir números en acciones concretas de producto

✅ Honestidad analítica: Reportar resultados negativos con la misma claridad que los positivos



📱 Análisis de Embudo de Conversión y Pruebas A/B en App Móvil
Análisis de datos completo de comportamiento de usuarios en aplicación móvil — desde la exploración del embudo de conversión hasta pruebas A/A/A/B rigurosas para validar cambios de UI.
Proyecto orientado a la toma de decisiones basada en evidencia estadística.


Este proyecto analiza el comportamiento de usuarios en una aplicación móvil de comercio electrónico durante la primera semana de agosto de 2019. El objetivo principal fue evaluar si un cambio en el tamaño de fuente (interfaz de usuario) generaba un impacto real en el tráfico y la conversión de los usuarios.


El análisis incluye:

🔍 Exploración de datos — cobertura temporal y completitud

📊 Análisis de embudo de conversión — identificación de puntos de fuga

🧪 Pruebas A/A/B — validación estadística rigurosa con control doble

🛡️ Corrección de Bonferroni — protección contra falsos positivos


| Etapa                     | Conversión Acumulada | Pérdida Respecto a Etapa Anterior |
| ------------------------- | :------------------: | :-------------------------------: |
| Página Principal (inicio) |         100%         |                 —                 |
| Página de Ofertas         |       **39.6%**      |            🔴 **60.4%**           |
| Carrito                   |    ~47% del total    |               ~7.4%               |
| **Pago Completado**       |       **47.5%**      |               ~0.5%               |


Hallazgo Crítico

El 60.4% de los usuarios se pierden al pasar de la Página Principal a la Página de Ofertas. Esta es la etapa con mayor fuga del embudo y representa la oportunidad de mayor impacto para mejorar la retención.

📈 Resultados de las Pruebas Estadísticas

1️⃣ Prueba A/A (Validación de Controles)
| Métrica          | Valor                   | Interpretación                                  |
| ---------------- | ----------------------- | ----------------------------------------------- |
| **Z-statístico** | 1.966                   | Límite de significancia                         |
| **Valor p**      | 0.0493                  | ~0.05 (zona gris)                               |
| **Decisión**     | ⚠️ **No se rechaza H₀** | Los controles son estadísticamente equivalentes |

2️⃣ Pruebas A/B (Grupo A vs Grupo B)

| Evento                 | Z-statístico |  Valor p  | α = 0.10 | Decisión        |
| ---------------------- | :----------: | :-------: | :------: | --------------- |
| `MainScreenAppear`     |       —      |   > 0.05  |     —    | No rechazar H₀  |
| `OffersScreenAppear`   |     1.705    | **0.088** |     ✅    | **Rechazar H₀** |
| `CartScreenAppear`     |     2.053    | **0.040** |     ✅    | **Rechazar H₀** |
| `PaymentScreenSuccess` |       —      |   > 0.05  |     —    | No rechazar H₀  |

3️⃣ Pruebas AA/B (Grupo AA vs Grupo B)

No hay evidencia suficiente para rechazar H₀


4️⃣ Corrección de Bonferroni

Para controlar la tasa de error familiar (family-wise error rate) al realizar múltiples comparaciones:

| Configuración    | α Original | α Ajustado (Bonferroni) | Eventos Significativos |
| :--------------- | :--------: | :---------------------: | :--------------------: |
| A/B (4 eventos)  |    0.10    |        **0.025**        |  1 (CartScreenAppear)  |
| A/B (4 eventos)  |    0.05    |        **0.0125**       |            0           |
| AA/B (4 eventos) |    0.10    |        **0.025**        |            0           |

✅ Veredicto final con Bonferroni: No hay diferencia significativa entre los grupos. Los resultados iniciales de A/B no resisten la corrección por múltiples comparaciones.

✅ Conclusión Final

🎯 ¿Funcionó el cambio de fuente?

NO. Después de limpiar los datos, filtrar al periodo válido (1–7 de agosto) y aplicar correcciones estadísticas rigurosas, se concluye que:
El cambio de tamaño de fuente fue INEFICIENTE para generar más tráfico o conversión dentro de la aplicación.

💡 Recomendaciones Estratégicas

Prioridad 1: Reducir la Fuga en la Página Principal → Ofertas (60.4%)

El problema NO es la fuente. El problema es que los usuarios no llegan a ver las ofertas.

🔥 Hacer más visible y atractiva la sección de ofertas desde la página principal

🎯 Implementar banners destacados o notificaciones push sobre promociones activas

🧪 A/B test: Probar diferentes ubicaciones y diseños del botón/link a ofertas

Prioridad 2: Recuperar Carritos Abandonados
Aunque la fuga Carrito → Pago es baja (~0.5%), el volumen de usuarios que añaden al carrito pero no pagan representa una oportunidad


💡 Investigar: 
¿Problemas técnicos en la pasarela? 

¿Falta de métodos de pago? 

¿Costos de envío inesperados?


Prioridad 3: Personalización y Segmentación

La mayoría de usuarios abandonan en la página principal, lo que sugiere que no encuentran contenido relevante


🎯 Propuesta: Realizar un estudio de segmentación para mostrar preferencias personalizadas que incentiven la compra

🛠️ Stack Tecnológico y Metodología

| Herramienta / Método            | Uso                                                |
| ------------------------------- | -------------------------------------------------- |
| **Python (Pandas, NumPy)**      | Limpieza y manipulación de datos                   |
| **SciPy (Z-test proporciones)** | Pruebas de significancia estadística               |
| **Matplotlib / Seaborn**        | Visualización de embudos y series temporales       |
| **Corrección de Bonferroni**    | Control de error tipo I en múltiples comparaciones |
| **Diseño A/A/A/B**              | Validación de aleatorización con doble control     |

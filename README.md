# 📈 Análisis del Precio Marginal Local (PML) a partir de la API del CENACE

Este proyecto en Python permite **consultar, visualizar y analizar** el Precio Marginal Local (PML) para un nodo específico del **Sistema Interconectado Nacional (SIN)**, utilizando la **API pública del CENACE** (Centro Nacional de Control de Energía) en México.

---

## 🧰 Funcionalidades

- 🔎 Consulta del PML por nodo y rango de fechas.
- 📊 Visualización gráfica del comportamiento horario del PML.
- 📈 Análisis estadístico básico: media diaria, máximos y mínimos.
- ✅ Corrección del valor horario `"24"` para manejo adecuado de la medianoche.
- 🧩 Descomposición del PML en sus componentes: energía, pérdidas y congestión.

---

# 🧠 Estructura del código

obtener_datos_pml(id_nodo, fecha_objetivo)
Descarga los datos de PML para un nodo en una fecha específica.

obtener_rango_pml(id_nodo, fecha_inicio, fecha_fin)
Itera sobre un rango de fechas, acumulando los datos diarios.

graficar_rango_pml(df, id_nodo, fecha_inicio, fecha_fin)
Genera una gráfica del PML a lo largo del tiempo.

analizar_rango_pml(df, id_nodo)
Imprime estadísticas como media, máximos y mínimos del PML.

---

# 🧪 Ejemplo de uso
python
Copy
Edit
from datetime import date

NODO_ID = '01PLO-115'
FECHA_INICIO_RANGO = date(2025, 7, 10)
FECHA_FIN_RANGO = date(2025, 7, 16)

df = obtener_rango_pml(NODO_ID, FECHA_INICIO_RANGO, FECHA_FIN_RANGO)

if not df.empty:
    graficar_rango_pml(df, NODO_ID, FECHA_INICIO_RANGO, FECHA_FIN_RANGO)
    analizar_rango_pml(df, NODO_ID)

---

# 📷 Visualización
La función graficar_rango_pml genera una figura como la siguiente:

yaml
Copy
Edit
Eje X: Fecha y hora  
Eje Y: PML en $/MWh  
Línea: Evolución horaria del PML
Incluye etiquetas, leyendas y formato de fecha legible.

---

# 🧾 Glosario
Término	Descripción

PML	Precio Marginal Local

CENACE	Centro Nacional de Control de Energía

SIN	Sistema Interconectado Nacional

PML_ENE	Componente del PML asociado al costo de la energía

PML_PER	Componente del PML asociado a las pérdidas en la red

PML_CNG	Componente del PML asociado a la congestión de la red

---

# 📌 Notas adicionales
Este proyecto está enfocado en datos del Mercado Eléctrico Mayorista (MEM) en México.

El código maneja errores comunes como fallos de conexión o respuestas vacías.

Puede adaptarse fácilmente a otros nodos o sistemas regionales.

Ideal para análisis exploratorios, reportes o visualización educativa.

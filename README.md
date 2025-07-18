📈 Análisis de Precio Marginal Local (PML) desde la API de CENACE
Este proyecto permite consultar, visualizar y analizar el Precio Marginal Local (PML) para un nodo específico del Sistema Interconectado Nacional (SIN) utilizando la API pública del CENACE (Centro Nacional de Control de Energía) de México.

🚀 Características principales
Consulta de datos horarios de PML (y sus componentes: energía, pérdidas y congestión) para una fecha o rango de fechas.

Manejo correcto de la hora "24" (medianoche) para asegurar series temporales consistentes.

Visualización gráfica del comportamiento del PML.

Estadísticas básicas: resumen descriptivo, promedio diario, horas con PML máximo y mínimo.

📦 Librerías utilizadas
bash
Copy
Edit
requests
pandas
matplotlib
bs4 (BeautifulSoup)
datetime
Puedes instalarlas con:

bash
Copy
Edit
pip install -r requirements.txt
⚠️ Recuerda que la API de CENACE devuelve los datos en formato XML, por lo que se utiliza BeautifulSoup para su procesamiento.

🧠 Estructura del código
obtener_datos_pml: Descarga y procesa los datos XML para una fecha.

obtener_rango_pml: Itera sobre un rango de fechas, consolidando los datos en un único DataFrame.

graficar_rango_pml: Genera una gráfica del PML a lo largo del rango temporal.

analizar_rango_pml: Muestra estadísticas descriptivas del comportamiento del PML.

📊 Ejemplo de uso
python
Copy
Edit
if __name__ == "__main__":
    NODO_ID = '01PLO-115'
    FECHA_INICIO_RANGO = date(2025, 7, 10)
    FECHA_FIN_RANGO = date(2025, 7, 16)

    df = obtener_rango_pml(NODO_ID, FECHA_INICIO_RANGO, FECHA_FIN_RANGO)

    if not df.empty:
        graficar_rango_pml(df, NODO_ID, FECHA_INICIO_RANGO, FECHA_FIN_RANGO)
        analizar_rango_pml(df, NODO_ID)
📷 Visualización
La gráfica generada muestra la evolución horaria del Precio Marginal Local durante el rango analizado:

java
Copy
Edit
Fecha y hora (X-axis) vs PML en $/MWh (Y-axis)
🧾 Notas adicionales
El script maneja errores de conexión y respuestas no exitosas de la API.

Se ajustan correctamente las horas "24", que representan la medianoche del día siguiente.

Ideal para análisis exploratorio de precios nodales y estudios de comportamiento del mercado eléctrico mexicano.

📚 Glosario
Término	Significado
PML	Precio Marginal Local
CENACE	Centro Nacional de Control de Energía
SIN	Sistema Interconectado Nacional
PML_ENE	Componente del PML asociado al costo de energía
PML_PER	Componente del PML asociado a las pérdidas
PML_CNG	Componente del PML asociado a la congestión de red

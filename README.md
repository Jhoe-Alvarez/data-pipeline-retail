📊 Pipeline de Datos y Dashboard de Ventas Retail
Este proyecto implementa un pipeline de datos completo para analizar información de ventas retail/e-commerce. El flujo incluye limpieza y transformación de datos con Python (Google Colab), exportación a un CSV limpio y visualización de KPIs en un dashboard interactivo en Power BI.
🚀 Objetivos
• Mostrar habilidades en ETL (Extract, Transform, Load) con Python.
• Crear un dataset limpio y estructurado listo para análisis.
• Construir un dashboard interactivo en Power BI con indicadores clave del negocio.
🛠️ Tecnologías usadas
• Python (Pandas, NumPy) → limpieza y transformación de datos.
• Google Colab → ejecución del ETL.
• Power BI Desktop → visualización de datos y creación del dashboard.
• GitHub → publicación del proyecto.
📂 Estructura del repositorio
data-pipeline-retail/
├─ data/
│  ├─ raw/                # Dataset original
│  └─ processed/          # Dataset limpio (superstore_clean.csv)
├─ notebook/
│  └─ Retail_ETL_Colab_to_CSV.ipynb
├─ dashboard/
│  └─ Retail_Dashboard.pbix
├─ screenshots/
│  └─ dashboard_overview.png
└─ README.md
🔄 Pipeline de datos (ETL)
1. Carga del dataset
import pandas as pd

df = pd.read_csv("superstore.csv", encoding="utf-8")
print(df.shape)
df.head()
2. Limpieza de columnas
# Normalizar nombres de columnas
df.columns = df.columns.str.strip().str.replace(" ", "_")

# Convertir fechas
df["OrderDate"] = pd.to_datetime(df["OrderDate"], errors="coerce")
df["ShipDate"] = pd.to_datetime(df["ShipDate"], errors="coerce")

# Convertir numéricos
for col in ["Sales", "Profit", "Discount", "Quantity"]:
    df[col] = pd.to_numeric(df[col], errors="coerce")
3. Manejo de nulos y duplicados
# Eliminar filas sin valores clave
df = df.dropna(subset=["OrderID", "OrderDate", "CustomerID", "ProductID", "Sales", "Quantity"])

# Rellenar nulos no críticos
df["Discount"] = df["Discount"].fillna(0)
df["Profit"] = df["Profit"].fillna(0)
df = df.drop_duplicates(subset=["OrderID", "ProductID"])
4. Features adicionales
import numpy as np

df["UnitPrice"] = np.where(df["Quantity"] > 0, df["Sales"] / df["Quantity"], 0)
df["MarginPct"] = np.where(df["Sales"] != 0, df["Profit"] / df["Sales"], 0)
df["YearMonth"] = df["OrderDate"].dt.to_period("M").astype(str)
5. Exportación del dataset limpio
df.to_csv("superstore_clean.csv", index=False)
print("Archivo limpio guardado:", "superstore_clean.csv")
📊 Dashboard en Power BI
KPIs principales:
- 💰 Total Sales = SUM(Sales)
- 📈 Total Profit = SUM(Profit)
- 📦 Total Quantity = SUM(Quantity)
- 📊 Margin % = DIVIDE([Total Profit], [Total Sales])
- 🛒 Avg Ticket = DIVIDE([Total Sales], DISTINCTCOUNT(OrderID))
Visualizaciones:
- 📉 Ventas mensuales por fecha.
- 🏆 Top 10 productos más vendidos.
- 👥 Clientes frecuentes (ventas y órdenes).
- 🍩 Participación por categoría.
- 🎛️ Segmentadores: Año, Región, Categoría, Segmento.
🧠 Insights obtenidos
• Identificación de picos de ventas en determinados meses.
• Productos más vendidos y rentables.
• Clientes más frecuentes y ticket promedio.
• Categorías con mayor participación en las ventas.
📥 Cómo usar este proyecto
1. Clona este repositorio:
git clone https://github.com/tu_usuario/data-pipeline-retail.git
2. Abre el notebook en Google Colab y ejecuta el ETL.
3. Usa el archivo superstore_clean.csv como fuente en Power BI Desktop.
4. Explora y personaliza el dashboard según tus necesidades.
👨‍💻 Autor
Tu Nombre
📧 tuemail@correo.com
🔗 LinkedIn | GitHub

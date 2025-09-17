import streamlit as st
import pandas as pd
import seaborn as sb
import matplotlib.pyplot as plt

# Page config
st.set_page_config(page_title="Car Explorer", page_icon="🚗", layout="wide")

# Load dataset
df = pd.read_csv("CARS.csv")

# Title and description
st.markdown("<h1 style='text-align: center; color: #ff4b4b;'>🚗 Car Brand & Model Explorer</h1>", unsafe_allow_html=True)
st.write("Explore horsepower and other attributes of different car brands interactively!")

# Sidebar
st.sidebar.header("⚙️ Filters")

# Brand selector
brands = df["Make"].unique()
selected_brand = st.sidebar.selectbox("Select a Car Brand", brands)

# Metric selector
numeric_columns = df.select_dtypes(include=["int64", "float64"]).columns.tolist()
selected_metric = st.sidebar.selectbox("Select Metric to Compare", numeric_columns, index=numeric_columns.index("Horsepower") if "Horsepower" in numeric_columns else 0)

# Filter data
s = df[df["Make"] == selected_brand]

# Car image (if you want placeholder for now)
st.image("https://cdn-icons-png.flaticon.com/512/743/743007.png", width=100, caption=f"{selected_brand} Cars")

# Plot
fig, ax = plt.subplots(figsize=(12, 6))
palette = sb.color_palette("coolwarm", len(s))  # colorful palette
sb.barplot(x="Model", y=selected_metric, data=s, ax=ax, palette=palette)

plt.xticks(rotation=90)
plt.title(f"{selected_brand}: {selected_metric} Comparison", fontsize=14, color="navy")
plt.xlabel("Car Model", fontsize=12)
plt.ylabel(selected_metric, fontsize=12)

# Show plot
st.pyplot(fig)

# Optional: show data table
with st.expander("📋 View Raw Data"):
    st.dataframe(s)

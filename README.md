import streamlit as st
import pandas as pd

# Beispielhafte Daten für die App
schichten = pd.DataFrame({
    'Datum': ['2025-02-24', '2025-02-25', '2025-02-26'],
    'Mitarbeiter': ['Debbie', 'Hümi', 'Robin'],
    'Schicht': ['Früh', 'Spät', 'Früh'],
    'Status': ['Geplant', 'Geplant', 'Offen']
})

st.title("Team-Schichtplaner")

# Schichtverwaltung
st.header("Schichtverwaltung")
st.dataframe(schichten)

# Möglichkeit zur Änderung von Schichten
mitarbeiter = st.selectbox("Mitarbeiter wählen", schichten['Mitarbeiter'].unique())
neue_schicht = st.selectbox("Neue Schicht wählen", ['Früh', 'Spät', 'Offen'])

if st.button("Schicht aktualisieren"):
    schichten.loc[schichten['Mitarbeiter'] == mitarbeiter, 'Schicht'] = neue_schicht
    st.success(f"Schicht für {mitarbeiter} geändert auf {neue_schicht}")
    st.dataframe(schichten)

# Planungshilfe
st.header("Planungshilfe")
st.text("Hier könnten Präferenzen und Homeoffice-Zeiten angezeigt werden")

# Team-Übersicht
st.header("Team-Übersicht")
st.text("Hier könnte die Skill-Matrix dargestellt werden")

# Urlaubsverwaltung
st.header("Urlaubsverwaltung")
st.text("Anzeige geplanter Urlaube für 2024 und 2025")

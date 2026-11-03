# Widget de seguridad pública — El Observador

¿Qué tan probable es que alguien con tu perfil apoye la mano dura, la cadena
perpetua, la pena de muerte o la humillación de los presos? Estimación con la
encuesta El Observador-UMAD-Ferreira sobre seguridad pública (mayo de 2026).

- **Widget:** https://observador-seguridad.streamlit.app/
- **Metodología completa** (modelo, intervalos, diagnósticos, pendientes):
  [`widgets/seguridad/WIDGET_README.md`](widgets/seguridad/WIDGET_README.md)

Regresión logística ponderada (ridge) por pregunta, con edad, sexo, región,
nivel educativo, autoidentificación ideológica y victimización como predictores.
Los intervalos salen de un bootstrap estratificado. Los modelos ya entrenados
están en `widgets/seguridad/modelos/`.

**La base** está en `data/`:
- `base_etiquetada.csv`: la que usa el entrenamiento (con `peso_final`).
- `base_etiquetada_SEGURIDAD_para_probabilidad.xlsx`: el recorte con las
  columnas de las cuatro preguntas y los cortes.

```bash
pip install -r requirements.txt
streamlit run widgets/seguridad/app.py
pytest widgets/seguridad/tests
SEGURIDAD_DATA_FILE=data/base_etiquetada.csv python widgets/seguridad/train_model.py
```

Separado del repo del widget del IVE
([ive-widget-observador](https://github.com/Juanpintoselso33/ive-widget-observador)),
con su historia de commits.

Análisis y desarrollo: Juan Ignacio Pintos Elso.

---

# Public safety widget — El Observador

How likely is someone with your profile to support tough-on-crime politicians,
life imprisonment, the death penalty or the humiliation of prisoners? Estimated
from the El Observador-UMAD-Ferreira public safety survey (May 2026).

One weighted ridge logistic regression per question; predictors are age, sex,
region, education, ideological self-placement and crime victimization. Intervals
come from a stratified bootstrap. The survey data is in `data/` and the trained
models in `widgets/seguridad/modelos/`. Full methodology (in Spanish) in
[`widgets/seguridad/WIDGET_README.md`](widgets/seguridad/WIDGET_README.md).

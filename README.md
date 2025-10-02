# Offseek: Adversarial Pattern Generator

## Descripción

Offseek es un proyecto de investigación que explora la generación de patrones adversariales contra sistemas de reconocimiento facial mediante técnicas de visión por computador. El código genera patrones visuales complejos (hyperface patterns) que pueden confundir o saturar algoritmos de detección facial al superponer múltiples rostros distorsionados en una única imagen.

Este trabajo surge como respuesta al creciente despliegue de sistemas de vigilancia biométrica en espacios públicos, donde la recopilación masiva de datos biométricos ocurre sin consentimiento explícito ni control individual.

## Contexto

La infraestructura de smart cities actual integra miles de cámaras con capacidades de reconocimiento facial. Según datos públicos:

- **Londres** cuenta con más de 690,000 cámaras CCTV (aproximadamente 1 cámara por cada 13 habitantes)
- **Pekín** ha desplegado más de 470,000 cámaras con capacidad de reconocimiento facial
- Ciudades como **Nueva York**, **San Francisco** y múltiples municipios europeos han implementado o están evaluando sistemas similares

Estos sistemas operan continuamente, generando perfiles biométricos sin que los ciudadanos tengan control sobre:
- Quién captura sus datos
- Dónde se almacenan
- Cómo se utilizan
- Cuánto tiempo se retienen

## Objetivo del Proyecto

Desarrollar algoritmos capaces de generar patrones adversariales aplicables a elementos físicos (ropa, accesorios, tejidos) que actúen como contramedida técnica ante la vigilancia biométrica indiscriminada. El objetivo no es la invisibilidad, sino recuperar la capacidad de decisión sobre la propia exposición biométrica.

## Funcionamiento Técnico

El código implementa las siguientes etapas:

### 1. Preparación del Dataset
- Utiliza el dataset LFW (Labeled Faces in the Wild)
- Procesa hasta 1000 imágenes faciales
- Normaliza y redimensiona rostros a 128x128 píxeles

### 2. Generación del Patrón Adversarial

El algoritmo aplica múltiples transformaciones:

- Superposición de 200 rostros con transparencias variables (α = 0.1-0.5)
- Escalado aleatorio (0.5x - 1.5x)
- Rotación angular (-30° a +30°)
- Posicionamiento estocástico en canvas de 512x512 píxeles

### 3. Distorsiones Psicodélicas

Aplica transformaciones para aumentar la complejidad visual:

- **Ruido gaussiano**: σ = 25, simula interferencia de captura
- **Desenfoque**: kernel 5x5 para suavizar transiciones
- **Distorsión sinusoidal**: Desplazamiento espacial basado en funciones trigonométricas
- **Saturación de color**: Incremento del 50% en canal HSV

## Requisitos
```bash
pip install opencv-python numpy matplotlib pillow tqdm


## Dataset necesario: LFW-deepfunneled (~173MB)

Uso
Instalación
```bash
git clone https://github.com/tu-usuario/offseek.git
cd offseek
pip install -r requirements.txt


# Ejecutar el generador
python hyperface_generator.py
El patrón generado se guardará en hyperface_patterns/psychedelic_hyperface.jpg
Estructura del Proyecto

offseek/
├── hyperface_generator.py      # Script principal
├── requirements.txt            # Dependencias
├── README.md                   # Este archivo
├── LICENSE                     # Licencia MIT
└── hyperface_patterns/         # Patrones generados
    └── psychedelic_hyperface.jpg

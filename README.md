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
```

## Dataset necesario: LFW-deepfunneled (~173MB)


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

## Limitaciones Conocidas

Efectividad variable: Los patrones funcionan mejor contra sistemas de detección facial clásicos (Haar Cascades, HOG) que contra redes neuronales profundas modernas
Condiciones de uso: La eficacia depende de distancia, ángulo de captura, iluminación y resolución de la cámara
Contramedidas: Los sistemas pueden adaptarse mediante reentrenamiento adversarial
Legalidad: El uso de estas técnicas puede estar regulado según jurisdicción

## Marco Ético y Legal
Este proyecto se enmarca en la investigación de seguridad y privacidad. Los usuarios deben:

Verificar la legalidad en su jurisdicción antes de aplicar estos patrones en público
Considerar que el uso de contramedidas puede llamar más atención que la vigilancia pasiva
Entender que la privacidad efectiva requiere cambios sistémicos, no solo soluciones técnicas individuales

## Próximos Pasos

 Evaluación cuantitativa contra sistemas comerciales (Face++, Azure Face API, AWS Rekognition)
 Optimización para impresión en textiles manteniendo propiedades adversariales
 Análisis de resistencia a diferentes distancias y ángulos de captura
 Exploración de patrones dinámicos (mediante LEDs o e-textiles)

## Referencias Técnicas

Sharif et al. (2016) - "Accessorize to a Crime: Real and Stealthy Attacks on State-of-the-Art Face Recognition"
Wu et al. (2020) - "Making an Invisibility Cloak: Real World Adversarial Attacks on Object Detectors"
Komkov & Petiushko (2021) - "AdvHat: Real-world adversarial attack on ArcFace Face ID system"

## Contribuciones
Este es un proyecto de investigación abierto. Las contribuciones son bienvenidas mediante pull requests que:

Mejoren la efectividad de los patrones
Añadan evaluaciones empíricas
Documenten casos de uso reales
Aporten perspectivas legales o éticas

## Licencia
MIT License - Ver archivo LICENSE para detalles

### Nota: La privacidad es un derecho fundamental. Este proyecto no promueve actividades ilegales, sino que busca restaurar el equilibrio de poder entre individuos y sistemas de vigilancia masiva mediante herramientas técnicas accesibles.
Autor
Proyecto desarrollado como parte de la investigación en privacidad y seguridad biométrica.
Contacto
Para preguntas, sugerencias o colaboraciones, abre un issue en este repositorio.

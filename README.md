# Sign-language-detector
Detección de lenguaje de señas a partir de video


# Guia de ejecución

1. Seguir los pasos en el video(video)[https://www.youtube.com/watch?v=QC9GTb6Wsb4]

2. En el minuto 10:00 (video)[https://www.youtube.com/watch?v=QC9GTb6Wsb4&t=10m], cuando se esté configurando el CMake no olvidar activar el PYTHON_BUILD (esto habilita el API de Python necesario para el uso del notebook)

3. Compilación: 
   - En el visual studio seleccionar el proyecto pyopenpose como Main
   - Cambiar Debug a Release en Local Window Debugger
   
![compilacion](https://github.com/bogos/sign-language-detector/blob/master/images/compilation.png?raw=true)


4. Copiar los siguientes files generados, dentro del folder "openpose" de este proyecto
    - build/bin/*
    - build/x64/Release/openpose.dll
    - build/python/openpose/*

![copyfiles](https://github.com/bogos/sign-language-detector/blob/master/images/copy_files.png?raw=true)

5. Copiar los files de la carpeta "models" de openpose dentro de la carpeta "models" de este proyecto:
    - openpose/models/*

![models](https://github.com/bogos/sign-language-detector/blob/master/images/copiar_models.png?raw=true)

6. Abrir y correr "Flujo de Interpretacion de Lenguaje de Señas"

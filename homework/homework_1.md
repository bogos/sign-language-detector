# Tarea 1: 

Generar tablas con la siguiente información:

- La tabla se generará a partir de los videos de la carpeta "Videos"
- La tabla contara con las columnas Palabra, Alfa, # de Frames y # de Frames Sumarizados
- La corrida de la tabla debe ser N veces, cambiando el valor de alfa (ejm. Puedes correr alfa en intervalos 0.10)
- Crear un nuevo notebook y con el nuevo código
- Almacenar la informacion de las tablas en un csv

## Ejemplo Tabla

Para alfa = 0.95

|Palabra | Alfa | # de Frames originales | # de Frames Sumarizados|
|:------: | :-----:| :----------------------: | :-----------------------: |
|"Hola" | 0.95 | 30 | 6|
|"Adios" | 0.95 | 45| 7|
|"BuenosDias" | 0.95 | 35| 8|
|"Chau" | 0.95 | 37| 3|
|"Saludos" | 0.95 | 45| 4|

Para alfa = 0.85

|Palabra | Alfa | # de Frames originales | # de Frames Sumarizados|
|:------: | :-----:| :----------------------: | :-----------------------: |
|"Hola" | 0.85 | 30 | 4|
|"Adios" | 0.85 | 45| 3|
|"BuenosDias" | 0.85 | 35| 5|
|"Chau" | 0.85 | 37| 7|
|"Saludos" | 0.85 | 45| 3|

Para alfa = 0.75

|Palabra | Alfa | # de Frames originales | # de Frames Sumarizados|
|:------: | :-----:| :----------------------: | :-----------------------: |
|"Hola" | 0.75 | 30 | 4|
|"Adios" | 0.75 | 45| 3|
|"BuenosDias" | 0.75 | 35| 5|
|"Chau" | 0.75 | 37| 7|
|"Saludos" | 0.75 | 45| 3|

y así sucesivamente 
.
.
.

## Notas 
El código está implementado a un 80% solo hay que acomodar la información:

Se encuentra en Jupiter en la Seccion "Video Summarization"

```
# Notes:
# Its necessary to crop the video to detail when the gesture begins

# TODO:
# Add Folder/File readers

videoList = ["Adios","BuenosDias", "Hola", "Saludos", "Chau"]

vidcap = cv2.VideoCapture(f"./Videos/{videoList[-1]}.mp4")

// CODIGO PARA SUMARIZACION DE VIDEO:
while existFrame: 
    if(count == 0):
      vidcap.set(cv2.CAP_PROP_POS_MSEC,sec*1000) # se toma el frame en el segundo
      hasFrames0, image0= vidcap.read() # se lee / hasframe-> boolean/ frameIni->image
      frameIni = image0
      vidArr.append(frameIni) # se almacena el frame inicial
      count = count + 1 # aumenta el contador
    else: 
      vidcap.set(cv2.CAP_PROP_POS_MSEC,sec*1000) # se toma el frame en el segundo
      hasFrames,image = vidcap.read() # se lee / hasframe-> boolean/ image->image

      if(image is not None):
        cm = np.corrcoef(frameIni.flat,image.flat)
        r = cm[0, 1]
        if(r < 0.95): # <=============================== ESTE ES EL ALFA (0.95)
          vidArr.append(image)
          frameIni = image

      sec = sec + frameRate
      sec = round(sec, 2)
      count = count + 1
      existFrame = hasFrames
        
height, width, layers = frameIni.shape
size = (width,height)
out = cv2.VideoWriter(f"./Videos/Summary/{videoList[-1]}.mp4",cv2.VideoWriter_fourcc(*'MP4V'), 5, size)

for i in range(0,len(vidArr)):
    out.write(vidArr[i])
out.release()

for i in range(0,len(vidArr)):
  plt.figure()
  plt.imshow(vidArr[i])
plt.show()  
```

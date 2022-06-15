# -WORDLE---words-game-structured-paradigm
the word game " ", which is basically developed by console, to make it easy to understand.
It is developed and documented so that it can be modified, to use a list or a text file "", with the limit that 5-letter words are used.



import random

#listaPalabras = ['ancla','brisa','choza','luces','robar','perro','buque','almas','hongo','fresa']  
#A=random.choice(listaPalabras) #usar el metodo choice para que la palabra aparesca de manera aleatoria


def adivinarPalabra (letraAdivinar,adivinar):  #Esta funcion es para validar y el uso de "def" es para definir la fuuncion 
    pClave = ""
    pos = 0

    for  texto in  adivinar:
        if texto ==  letraAdivinar[pos]:

            pClave +=[c for c in adivinar][pos]+"+ "  #implementacion de como funcina el metodo split 

            
        elif texto in  letraAdivinar:
            #pClave += "*"
            pClave +=[c for c in adivinar][pos]+"* " # se aplica igual aqui el split
        else :
            #pClave += "-"
            pClave +=[c for c in adivinar][pos]+"- "

            
        pos += 1
    print(pClave)
    return pClave == "+++++"

listaPalabras = []
documentoPalabras = open("palabras.txt")

for palabra in documentoPalabras:
    listaPalabras.append(palabra.strip())

A = random.choice(listaPalabras)





    
#palabra = random.choice(listaPalabras))
intentos = 0

adivinada = False

opcionArchivo= int(input("Desea usar otro archivo de configuración? (1 SÍ - 0 NO)  :"))


while  opcionArchivo  < 0  or opcionArchivo >1:
    opcionArchivo= int(input("Desea usar otro archivo de configuración? (1 SÍ - 0 NO)  :"))
if opcionArchivo == 0:
        print("el Archivo es config.txt ")
        nombreArchivo = "config.txt"
if opcionArchivo ==1:
        print("¿Cómo se llama tu archivo de configuración?")
        nombreArchivo = str(input())
    
print("el Archivo se llama: ",nombreArchivo+".txt")
    
    





while  intentos <=6 and not  adivinada:

    

     pAdivina = input("ingrese una palabra de  5 letras:  ")

     if pAdivina   in  listaPalabras:
        print("La  palabra",pAdivina,"si existe")
     if pAdivina not in listaPalabras:
        print("la palabra",pAdivina," no hace parte de la lista")

    
     cpalabra= len(pAdivina)
     if cpalabra > 5 :
        print("Se excedio con el numero de letras, ingrese otra palabra")
        
     elif cpalabra !=5:
        print("La palabra debe tener 5 letras, ingrese otra palabra")
        
     else:

        intentos += 1
        faltan = 6- intentos
        print("usted esta en el intento  Numero ",intentos,"  le quedan ", faltan )
        adivinada = adivinarPalabra(A,pAdivina)
    
     if intentos ==6: # termina los intentos 

        print("Has superado el limite de intentos ,la palabra correcta era:",A)
        break

     elif pAdivina==A:
        print(" Felicitaciones,has ganado, la palabra correcta es: ",A)
        exit()









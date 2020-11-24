# AES CIFRADOR

#biblioteca
from cryptography.fernet import Fernet

#Cargar clave
def cargar_clave():
	return open("clave.key","rb").read()

#Escribir y guardar clave
def genera_clave():
	clave=Fernet.generate_key()
	with open("clave.key","wb")as archivo_clave:
		archivo_clave.write(clave)


#Encriptar archivo
def encript(nom_archivo,clave):
	f=Fernet(clave)
	with open(nom_archivo, "rb")as file:
		archivo_info = file.read()
	encypted_data = f.encrypt(archivo_info)
	with open(nom_archivo,"wb")as file:
		file.write(encypted_data)

#Generar clave
genera_clave()
#cargar clave
clave = cargar_clave()

#encriptar archivo
nom_archivo = 'text.txt'
encript(nom_archivo,clave)

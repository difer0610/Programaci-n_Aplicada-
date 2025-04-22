import random
import csv
import time

# Abrimos (o creamos) un archivo CSV en modo append para no sobreescribir datos previos
with open("numeros_aleatorios.csv", mode="a", newline="") as archivo:
    writer = csv.writer(archivo)

    print("Generando números aleatorios entre 0 y 1 (sin incluir)...")
    print("Presiona Ctrl + C para detener el programa.")

    try:
        while True:
            numero = random.uniform(0, 1)  # Genera un número flotante entre 0 y 1
            while numero == 0 or numero == 1:
                numero = random.uniform(0, 1)  # Asegura que no sea ni 0 ni 1
            
            writer.writerow([numero])  # Escribe el número en una sola columna
            print(f"Número generado: {numero}")
            time.sleep(0.5)  # Espera medio segundo entre cada número (opcional)

    except KeyboardInterrupt:
        print("\nPrograma detenido con Ctrl + C.")

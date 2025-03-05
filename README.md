import tkinter as tk
from tkinter import messagebox
import math

def click(boton):
    expresion = entrada.get()
    try:
        if boton == "AC":
            entrada.set("")
        elif boton == "DEL":
            entrada.set(expresion[:-1])
        elif boton == "=":
            entrada.set(eval(expresion))
        elif boton == "√":
            entrada.set(math.sqrt(float(expresion)))
        elif boton == "^":
            entrada.set(expresion + "**")
        elif boton == "sin":
            entrada.set(math.sin(math.radians(float(expresion))))
        elif boton == "cos":
            entrada.set(math.cos(math.radians(float(expresion))))
        elif boton == "tan":
            entrada.set(math.tan(math.radians(float(expresion))))
        elif boton == "log":
            entrada.set(math.log10(float(expresion)))
        elif boton == "ln":
            entrada.set(math.log(float(expresion)))
        elif boton == "π":
            entrada.set(expresion + str(math.pi))
        elif boton == "e":
            entrada.set(expresion + str(math.e))
        elif boton == "x!":
            entrada.set(math.factorial(int(expresion)))
        else:
            entrada.set(expresion + str(boton))
    except:
        messagebox.showerror("Error", "Entrada no válida")

# Crear ventana
ventana = tk.Tk()
ventana.title("Calculadora Científica")
ventana.geometry("500x700")
ventana.configure(bg="#2E2E2E")

entrada = tk.StringVar()
pantalla = tk.Entry(ventana, textvariable=entrada, font=("Arial", 24), bd=10, relief=tk.SUNKEN, justify='right', bg="#000", fg="#FFF")
pantalla.pack(fill=tk.BOTH, ipadx=8, ipady=15, padx=5, pady=5)

botones = [
    "SHIFT", "ALPHA", "MODE", "(", ")",
    "OPTN", "CALC", "x^2", "√", "^",
    "log", "ln", "x!", "sin", "cos", "tan",
    "7", "8", "9", "+", "DEL",
    "4", "5", "6", "-", "AC",
    "1", "2", "3", "*", "/",
    "0", ".", "π", "e", "="
]

frame = tk.Frame(ventana, bg="#2E2E2E")
frame.pack()

row, col = 0, 0
for boton in botones:
    color = "#555" if boton in ["DEL", "AC"] else "#444"
    tk.Button(frame, text=boton, font=("Arial", 18), width=5, height=2, command=lambda b=boton: click(b), bg=color, fg="#FFF", relief=tk.RAISED, bd=3).grid(row=row, column=col, padx=5, pady=5)
    col += 1
    if col > 4:
        col = 0
        row += 1

ventana.mainloop()

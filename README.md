# Simple-Calculator-Using-GUI
from tkinter import *

calculation = " "

def add_calculation(symbol):
    global calculation
    calculation += str(symbol)
    equation_label.set(calculation)

def evaluate_calculation():
    global calculation

    try:

        total = str(eval(calculation))

        equation_label.set(total)

        calculation = total

    except SyntaxError:

        equation_label.set("syntax error")

        calculation = ""

    except ZeroDivisionError:

        equation_label.set("arithmetic error")

        calculation = ""

def clear():
    global calculation

    equation_label.set("")

    calculation = ""


window = Tk()
window.title("Calculator program")
window.geometry("500x500")


equation_label = StringVar()

label = Label(window, textvariable=equation_label, font=('consolas',20), bg="white", width=24, height=2)
label.pack()

frame = Frame(window)
frame.pack()

button1 = Button(frame, text=1, height=2, width=7, font=25,
                 command=lambda: add_calculation(1))
button1.grid(row=0, column=0)

button2 = Button(frame, text=2, height=2, width=7, font=25,
                 command=lambda: add_calculation(2))
button2.grid(row=0, column=1)

button3 = Button(frame, text=3, height=2, width=7, font=25,
                 command=lambda: add_calculation(3))
button3.grid(row=0, column=2)

button4 = Button(frame, text=4, height=2, width=7, font=25,
                 command=lambda: add_calculation(4))
button4.grid(row=1, column=0)

button5 = Button(frame, text=5, height=2, width=7, font=25,
                 command=lambda: add_calculation(5))
button5.grid(row=1, column=1)

button6 = Button(frame, text=6, height=2, width=7, font=25,
                 command=lambda: add_calculation(6))
button6.grid(row=1, column=2)

button7 = Button(frame, text=7, height=2, width=7, font=25,
                 command=lambda: add_calculation(7))
button7.grid(row=2, column=0)

button8 = Button(frame, text=8, height=2, width=7, font=25,
                 command=lambda: add_calculation(8))
button8.grid(row=2, column=1)

button9 = Button(frame, text=9, height=2, width=7, font=25,
                 command=lambda: add_calculation(9))
button9.grid(row=2, column=2)

button0 = Button(frame, text=0, height=2, width=7, font=25,
                 command=lambda: add_calculation(0))
button0.grid(row=3, column=0)

plus = Button(frame, text='+', height=2, width=7, font=25,
                 command=lambda: add_calculation('+'))
plus.grid(row=0, column=3)

minus = Button(frame, text='-', height=2, width=7, font=25,
                 command=lambda: add_calculation('-'))
minus.grid(row=1, column=3)

multiply = Button(frame, text='*', height=2, width=7, font=25,
                 command=lambda: add_calculation('*'))
multiply.grid(row=2, column=3)

divide = Button(frame, text='/', height=2, width=7, font=25,
                 command=lambda: add_calculation('/'))
divide.grid(row=3, column=3)

equal = Button(frame, text='=', height=2, width=7, font=25,
                 command=evaluate_calculation)
equal.grid(row=3, column=2)

decimal = Button(frame, text='.', height=2, width=7, font=25,
                 command=lambda: add_calculation('.'))
decimal.grid(row=3, column=1)

clear = Button(window, text='clear', height=2, width=10, font=25,
                 command=clear)
clear.pack()

window.mainloop()

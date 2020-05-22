from tkinter import *
from tkinter import messagebox
import math
flg=1
opr=""
def funno(i):
	i=str(i)
	if flg==1:
		dis1L.configure(text=dis1L.cget("text")+i)
	else:

		dis2L.configure(text=dis2L.cget("text")+i)

def clear():
	dis1L.configure(text="")
	dis2L.configure(text="")
	dis3L.configure(text="")
def cal(opt):
	global flg
	flg=1
	global opr
	if opt=='+' or opt=='-' or opt=='*' or opt=='/' or opt=="pow":
		flg=0
	opr=opt
def equal():
	global flg
	global res
	global opr
	if flg==0:

		a=float(dis1L.cget("text"))
		b=float(dis2L.cget("text"))

		if opr=='+':
			res=a+b
		elif opr=='-':
			res=a-b
		elif opr=='*':
			res=a*b	
		elif opr=='/':
			res=a/b
		elif opr=='pow':
			res=a**b
	else:
		a=float(dis1L.cget("text"))
		if opr=='sin':
			a=math.radians(a)
			res=math.sin(a)
		elif opr=='cos':
			a=math.radians(a)
			res=math.cos(a)				
		elif opr=='tan':
			a=math.radians(a)
			res=math.tan(a)
		elif opr=='loge':
			a=math.radians(a)
			res=math.log(a)
		elif opr=='log10':
			res=math.log10(a)
		elif opr=='sqrt':
			res=math.sqrt(a)
		elif opr=='factorial':
			res=math.factorial(a)
	dis3L.configure(text=res)
	flg=1					
				
				
def fraction():
	if flg==1:
		a=dis1L.cget("text")+'.'
		dis1L.configure(text=a)
	else:
		b=dis2L.cget("text")+'.'
		dis2L.configure(text=b)	

root=Tk()

root.config(background="light green")
root.geometry('320x550')


root.title("CALCULATOR")
title=Label(root,text="CALCULATOR",bg="pink")
title.config(font=("curior",20))

no1L=Label(root,text="Enter no1 :",bg="light green")
no2L=Label(root,text="Enter no2:",bg="light green")
ansL=Label(root,text="Answer:",bg="light green")
'''
no1E=Entry(root)
no2E=Entry(root)
ansE=Entry(root)

no1E.grid(row=1 ,column=2,ipadx="100" ,padx="30",pady="10")
no2E.grid(row=2 ,column=2,ipadx="100" ,padx="30",pady="10")
ansE.grid(row=3 ,column=2,ipadx="100" ,padx="30",pady="10")
'''

dis1L=Label(root,text="",bg="white")
dis2L=Label(root,text="",bg="white")
dis3L=Label(root,text="",bg="white")

title.grid(row=0,column=0,columnspan=5)


no1L.grid(row=1,column=0,columnspan=2)
no2L.grid(row=2,column=0,columnspan=2)
ansL.grid(row=3,column=0,columnspan=2)

dis1L.grid(row=1,column=2,padx="10",ipadx="50",pady="10",columnspan=3)
dis2L.grid(row=2,column=2,padx="10",ipadx="50",pady="10",columnspan=3)
dis3L.grid(row=3,column=2,padx="10",ipadx="50",pady="10",columnspan=3)

Button(root,text="1",bg="light blue",command=lambda:funno(1)).grid(row=4,column=0,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="2",bg="light blue",command=lambda:funno(2)).grid(row=4,column=1,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="3",bg="light blue",command=lambda:funno(3)).grid(row=4,column=2,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="+",bg="orange",command=lambda:cal('+')).grid(row=4,column=3,ipadx="10",ipady="10",pady="10",padx="7")
Button(root,text="sin",bg="yellow",command=lambda:cal('sin')).grid(row=4,column=4,ipadx="10",ipady="10",padx="2")

Button(root,text="4",bg="light blue",command=lambda:funno(4)).grid(row=5,column=0,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="5",bg="light blue",command=lambda:funno(5)).grid(row=5,column=1,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="6",bg="light blue",command=lambda:funno(6)).grid(row=5,column=2,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="-",bg="orange",command=lambda:cal('-')).grid(row=5,column=3,ipadx="10",ipady="10",pady="10",padx="7")
Button(root,text="cos",bg="yellow",command=lambda:cal('cos')).grid(row=5,column=4,ipadx="10",ipady="10",padx="1")


Button(root,text="7",bg="light blue",command=lambda:funno(7)).grid(row=6,column=0,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="8",bg="light blue",command=lambda:funno(8)).grid(row=6,column=1,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="9",bg="light blue",command=lambda:funno(9)).grid(row=6,column=2,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="*",bg="orange",command=lambda:cal('*')).grid(row=6,column=3,ipadx="10",ipady="10",pady="10",padx="7")
Button(root,text="tan",bg="yellow",command=lambda:cal('tan')).grid(row=6,column=4,ipadx="10",ipady="10",padx="1")

Button(root,text="c",bg="orange",command=lambda:clear()).grid(row=7,column=0,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="0",bg="light blue",command=lambda:funno(0)).grid(row=7,column=1,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="=",bg="orange",command=lambda:equal()).grid(row=7,column=2,ipadx="10",ipady="10",pady="10",padx="10")
Button(root,text="/",bg="orange",command=lambda:cal('/')).grid(row=7,column=3,ipadx="10",ipady="10",pady="10",padx="7")
Button(root,text="pow",bg="yellow",command=lambda:cal('**')).grid(row=7,column=4,ipadx="10",ipady="10",padx="1")

Button(root,text="sqrt",bg="yellow",command=lambda:cal('sqrt')).grid(row=8,column=0,ipadx="2",ipady="10",padx="10")
Button(root,text="loge",bg="yellow",command=lambda:cal('loge')).grid(row=8,column=1,ipadx="2",ipady="10",padx="10")
Button(root,text="log10",bg="yellow",command=lambda:cal('log10')).grid(row=8,column=2,ipadx="2",ipady="10",padx="10")
Button(root,text="factorial",bg="yellow",command=lambda:cal('factorial')).grid(row=8,column=3,ipadx="2",ipady="10",pady="10",padx="7")
Button(root,text=".",bg="blue",command=fraction).grid(row=8,column=4,ipadx="14",ipady="10",padx="1")
Button(root,text="close",bg="yellow",command=root.destroy).grid(row=9,column=0,ipadx="120",ipady="10",padx="10",columnspan="5")


root.mainloop()

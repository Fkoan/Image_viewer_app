# Image_viewer_app
The code is for viewing images using tkinter pkg
#~ image viewer app

from tkinter import *
from tkinter import ttk
from PIL import ImageTk,Image

root = Tk()
try:
	root.iconbitmap('pics/my_nick_name.ico')
except Exception as e:
Pass
my_img1 = ImageTk.PhotoImage(Image.open("pics/Alyssa_1.jpg"))
my_img2 = ImageTk.PhotoImage(Image.open("pics/Alyssa_2.jpg"))
my_img3 = ImageTk.PhotoImage(Image.open("pics/Alyssa_3.jpg"))
my_img4 = ImageTk.PhotoImage(Image.open("pics/Alyssa_4.jpg"))
my_img5 = ImageTk.PhotoImage(Image.open("pics/best.jpg"))

my_img_list=[my_img1, my_img2, my_img3, my_img4, my_img5]

#~ for the pic views![Alyssa_1](https://github.com/user-attachments/assets/cdfdb28b-841c-4ede-a87d-842b586ff955)
![Alyssa_2](https://github.com/user-attachments/assets/dde720f8-1684-455c-bf60-dcf6b29fff61)
![Alyssa_3](https://github.com/user![Alyssa_3](https://github.com/user-attachments/assets/81827978-7945-44a3-9061-8f331d23a5a3)
-attachments/assets/3711bcb8-1f8a-4185-b51a-0e07f563e066)

my_label = Label(image=my_img_list[0])
my_label.grid(row=0, column=0, columnspan=3, padx=2, pady=2)
my_label.configure(bg='#000000')
#~ for the forward button
def forward(img_num):
	global my_label
	global button_backward
	global forward
	my_label.grid_forget()
	my_label = Label(image=my_img_list[img_num - 1])
#~ the forward is called again for update
	button_forward = Button(root, text=">>", command=lambda: forward(img_num + 1))
	button_backward = Button(root, text="<<", command=lambda: back(img_num - 1))

	if img_num == 4:
		button_forward = Button(root, state=DISABLED)
	 
#~ referencing the position of the buttons for update
	my_label.grid(row=0, column=0, columnspan=3, padx=2, pady=2)
	button_forward.grid(row=1, column=2)
	button_backward.grid(row=1, column=0)

#~ for the back button
def back(img_num):
	global my_label
	global button_backward
	global forward
	my_label.grid_forget()
	my_label = Label(image=my_img_list[img_num - 1])

#~ the forward is called again for update
	button_forward = Button(root, text=">>", command=lambda: forward(img_num + 1))
	button_backward = Button(root, text="<<", command=lambda: back(img_num - 1))

	if img_num == 1:
		button_backward = Button(root, state=DISABLED)

#~ referencing the position of the buttons for update
	my_label.grid(row=0, column=0, columnspan=3, padx=2, pady=2)
	button_forward.grid(row=1, column=2)
	button_backward.grid(row=1, column=0)
	

button_backward = Button(root, text="<<", command=lambda: back)
button_exit = Button(root, text="Exit", command=quit)
button_forward = Button(root, text=">>", command=lambda: forward(2))

button_backward.grid(row=1, column=0)
button_exit.grid(row=1, column=1)
button_forward.grid(row=1, column=2)

root.mainloop()

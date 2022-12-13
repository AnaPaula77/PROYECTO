# PROYECTO
Este es mi proyecto para el Bootcamp de programación desde cero - Código Facilito
ES UNA AGENDA DIRECTORIO CON TKINTER


import tkinter as tk 
from back import * 


def save():
    print("your contact has been saved")

def delete():
    print("Your contact has been deleted")


window = tk.Tk()
background = "#4099BF"
colortext= "#250F2E"
window.title("Agenda")
window.geometry("600x400")
window.configure(bg=background)
Label_Title = tk.Label(window,text="This is your agenda", background=background, fg="black", font=("Helvetica", 20)).place(x=200 , y=10)
label_name= tk.Label(window,text="Name: ", background=background, fg="black", font=("Helvetica", 20)).place(x=50 , y=50) 
box_name = tk.Entry(window,textvariable="  ").place(x=160, y=50)
label_username= tk.Label(window,text="Username:  ", background=background, fg="black", font=("Helvetica", 20)).place(x=50 , y=80) 
box_username = tk.Entry(window,textvariable="  ").place(x=160, y=80)
label_email= tk.Label(window,text="Email: ", background=background, fg="black", font=("Helvetica", 20)).place(x=50 , y=110) 
box_email = tk.Entry(window,textvariable="  ").place(x=160, y=110)
label_web= tk.Label(window,text="Web: ", background=background, fg="black", font=("Helvetica", 20)).place(x=50 , y=140) 
box_web = tk.Entry(window,textvariable="  ").place(x=160, y=140)

bottonSave = tk.Button(window,text="Save",command=save, bg="white", fg="black").place(x=180, y=200)

bottonDelete = tk.Button(window,text="Delete",command=delete, bg="white", fg="black").place(x=180, y=240)

window.mainloop()



class User:
    def __init__(self, name, username, email, web, id):
        self.name = name
        self.username = username
        self.email = email
        self.web = web
        self.id = id

    def get_attributes(self):
        return {'name': self.name, 'username': self.username, 'email': self.email, 'web': self.web, 'id': self.id}

    def change_attributes(self, new_info):
        self.name = new_info ['name']
        self.username = new_info ['username']
        self.email = new_info ['email']
        self.web = new_info ['web']
        self.save()

        
    def save(self):
        file = open(f"user{self.id}.txt", 'w+')
        file.write(str(self.get_attributes()))
        file.close()

users = {}

def create_user(name,username,email,web):
    user = User(name, username, email, web, len(users)+1)
    user.save()
    users[str(len(users)+1)] = users


def search_user(id):
    return users[str(id)]

def delete_user(list_id):
    for id in list_id:
        del users[str(id)]

print(users)
create_user("Maria Fernanda Gomez", "Mafe", "mafe@gmail.com", "mafe.com")
create_user("Lucia Martinez", "Lu98", "Lumar98@gmail.com", "luciamartinez.com")
create_user("Ana Barajas", "anba07", "abarajas@gmail.com", "construccionesana.com")

print(users)
for user, info in users.items():
    print(info.get_attributes())

print('the users 1 and 2 were deleted')
print(users)
for user, info in users.items():
    print(info.get_attributes())

users['3'].change_attributes({'name': 'name', 'username': 'username', 'email': 'email', 'web': 'web', 'id': 'id'})

print(users)
for user, info in users.items():
    print(info.get_attributes())

 




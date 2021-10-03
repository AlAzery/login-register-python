# login-register-python

````python 
    
    granted = False
def grant():
    global granted
    granted = True
def login(name,password):
    success = False
    file = open("db.txt","r")
    for i in file:
         a,b = i.split(",")
         b = b.strip()
         if(a==name and b==password):
             success = True
             break
    file.close()
    if(success):
        print("Login Successful")
        grant()
    else:
        print("wrong user name or password")
        
def register(name,password):
    file = open("db.txt","a")
    file.write("\n"+name+","+password)
    grant()
def access(option):
    global name
    if(option=="1"):
        name = input("Enter your name: ")
        password = input("Enter your password: ")
        login(name,password)
        
    else:
        print("Enter your name and password to register")
        name = input("Enter your name: ")
        password = input("Enter your password: ")
        register(name,password)

def begin():
    global option
    print("welcome to Termux")
    print("1 - login")
    print("2 - registrasi")
    option = input("$/: ")
    if(option!="1" and option!="2"):
        begin()
        
begin()
access(option)

if(granted):
    print("Welcome ", name)
    print("### USER DETAILS ###")
    print("Username: ",name)


    

    
````
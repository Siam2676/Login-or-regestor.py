#Login-or-regestor.py
FILE = "users.txt"
import os
import hashlib
def hash_pass(p):
    return hashlib.sha256(p.encode()).hexdigest()

def user_exists(u):
    if not os.path.exists(FILE):
        return False
    with open(FILE, "r") as f:
        for line in f:
            name, _ = line.strip().split("|")
            if name == u:
                return True
    return False

def register():
    os.system("cls" if os.name == "nt" else "clear")
    print("===== REGISTER =====")
    u = input("Username: ")
    if user_exists(u):
        print("User already exists!")
        input("Enter...")
        return

    p1 = input("Password: ")
    p2 = input("Confirm Password: ")

    if p1 != p2:
        print("Password not match!")
        input("Enter...")
        return

    with open(FILE, "a") as f:
        f.write(u + "|" + hash_pass(p1) + "\n")

    print("Registration Successful!")
    input("Enter...")

register()



def login():
    print("===== LOGIN =====")
    u = input("Username: ")
    p = input("Password: ")

#    hp = hash_pass(p)

    # 1. Check if the user file exists
    if not os.path.exists(FILE):
        print("No users found!")
        input(" Enter...")
        return

    # 2. Read file and verify login
    with open(FILE, "r") as f:
        for line in f:
            name, pwd = line.strip().split("|")
            if name == u and pwd == hash_pass (p):
                print("Login Successful!")
                dashboard(u)
                return
                
                
            #       if name != u and pwd != p () :
        print("Wrong username or password!")
        
        exit()
        return
    
        
        
        
    


def dashboard(user):
    os.system("cls" if os.name == "nt" else "clear")
    print(f"Welcome {user}!")
    input("Press enter to exit...")


login()
hash_pass('p')

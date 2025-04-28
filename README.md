"# ATM-Checker" 
acc_details = {"6234001" :["user_1", 5000,8999],
               "6234002" :["user_2", 500, 9999],
               "6234003" :["user_3",1500,3535],
               "6234004" :["user_4",2000,1999],
               "6234005" :["user_5",1000,9090]}

print("*******#########*********")
print("Welcome to the ATM")
print("*******#########*********")
transaction_list =[]
max_attemts = 3
attempts = 0
print("insert the card..........")
user_acc_no = input("enter the acc.no : ")
while attempts < max_attemts:
    
    user_acc_pin = int(input("enter the acc.pin : "))
    if user_acc_pin == acc_details[user_acc_no][-1]:
                       print("correct pin. please proceed with transaction")
                       
                       

    else:
        attempts +=1
        remaining_attempts = max_attemts - attempts

        if remaining_attempts == 0:
            print("*******    Account locked. visit the branch     *******")
            break
    while True:
        print("choose an option : \n\
                                 1) Deposit\n\
                                 2) Withdraw\n\
                                 3) Check balance\n\
                                 4) Transaction History\n\
                                 5) pin change\n\
                                 6) Exit")
        option = int(input("choose an option number : "))
        if option == 1:
            amount = int(input("enter the amount : ($500,$1000,etc..)   "))
            acc_details[user_acc_no][1] += amount
            print(f"Total balance amount is : {acc_details[user_acc_no][1]}")
            transaction_list.append(f"Deposited rs.{amount} ")
                               
        elif option == 2:
            amount = int(input("enter the amount : ($500,$100)   "))
            if acc_details[user_acc_no][1] < amount:
                print("Insufficient Funds")
            else:
                acc_details[user_acc_no][1] -= amount
                print(f"Total balance amount is : {acc_details[user_acc_no][1]}")
                transaction_list.append(f"Withdraw rs.{amount} ")

                                
        elif option == 3:
            print(f"your balance :  {acc_details[user_acc_no][1]}")
                                     
        elif option == 4:
            print(f"Transaction History  :  {transaction_list}")
                               
        elif option == 5:
            new_pin = int(input("enter the new pin :  "))
            acc_details[user_acc_no][2] = new_pin
            print(f"Pin is changed : {acc_details[user_acc_no][2]}")
                               
        elif option == 6:
            break
        else:
            print("enter the vaild choice number ")
    break                  

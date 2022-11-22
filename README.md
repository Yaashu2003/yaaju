# yaaju
#website blocker 
 #Import libraries
import time
from datetime import datetime

host_path="C:\Windows\System32\drivers\etc\hosts"

redirect="127.0.0.1"   # IP adress(Can be found in command prompt)
#------------------------------------------------------------------------
#Add the website you want to block, in this list
websites=["www.youtube.com","youtube.com", "www.facebook.com", "facebook.com","web.whatsapp.com"]
#------------------------------------------------------------------------
sd = datetime(2022,11,30)   #start date
ed = datetime(2022,11,25)   #end date
td = datetime(datetime.now().year,datetime.now().month,datetime.now().day)  #today date

while True:
    if sd <= td < ed:
        with open(host_path,"r+") as file:
            content = file.read()
            for site in websites:
                if site in content:
                    pass
                else:
                    file.write(redirect+" "+site+"\n")
        print("All sites are blocked")
        break
        
    else: #  end_date < today_date
        with open(host_path,"r+") as file:
            content = file.readlines()
            file.seek(0)
            for line in content:
                if not any (site in line for site in websites):
                    file.write(line)
            file.truncate()
        print ("All sites unblocked")
        break 

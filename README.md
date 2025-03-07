# Parcial-Estructura-de-datos


import requests, re, json
from collections import Counter

IPS =[]
Errors = []

def extractIPS(regex, data):
    if data:
        return re.findall(regex, data.read())
    return None
  
data = open('C:/Users/Public/Parcial ED/access.log', "r")
regex = r"(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})"

resultado = extractIPS(regex, data)

for ip in resultado:
    if ip not in IPS:
      IPS.append(f"{ip}")
      print(f"IP: {ip}")   
    else:
     continue




def extractErrors(regex2, data2):
    if data2:
        return re.findall(regex2, data2.read())
    return None
  
data2 = open('C:/Users/Public/Parcial ED/access.log', "r")
regex2 = r'"\s(\d{3})'

resultado2 = extractErrors(regex2, data2)

for error in resultado2:
    if error not in Errors:
      Errors.append(f"Error {error}")   
    else:
       Errors.append(f"{error}")
    ErroresTotales = Counter(Errors)

print(json.dumps(ErroresTotales, indent =4))

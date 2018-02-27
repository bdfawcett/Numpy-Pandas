

```python
"""

Analysis

The temperatures in the southern hemisphere are currently warmer than those in the northern hemisphere.
    - This is expected since it is currently summer in the southern hemisphere and winter in the northern hemisphere.
Most cities currently have a humidity above 50% with more of the cities closest to the equator clustered together near 100%.
The current wind speed is fairly mild with most cities currently experiencing wind speeds under 15 mph.
    - The highest wind speeds are being experienced in the far northern hemisphere.
    
"""
```


```python
# Dependencies
import matplotlib.pyplot as plt
import requests as req
import pandas as pd
from citipy import citipy
import random
```


```python
cities = []
```


```python
# Save config information.
with open("../API_key.txt") as key:
    api_key = key.readlines()
url = "http://api.openweathermap.org/data/2.5/weather?"
units = "imperial"
```


```python
# Build partial query URL
query_url = url + "appid=" + api_key[0] + "&units=" + units + "&q="
query_url
```




    'http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q='




```python
while len(cities) < 500:
    rand_lat = random.randint(-90, 90)
    rand_lon = random.randint(-180, 180)
    #print(rand_lat, rand_lon)
    city = citipy.nearest_city(rand_lat, rand_lon)
    temp = []
    temp.append(req.get(query_url + city.city_name).json())
    validate_city = [data.get("cod") for data in temp]
    if validate_city[0] == 200:
        if city.city_name not in cities:
            cities.append(city.city_name)
            print("Processing Record " + str(len(cities)) + "- " + city.city_name)
            print(query_url + city.city_name)
#print(cities)
```

    Processing Record 1- sao filipe
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sao filipe
    Processing Record 2- carnarvon
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=carnarvon
    Processing Record 3- dikson
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dikson
    Processing Record 4- vaini
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vaini
    Processing Record 5- ahipara
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ahipara
    Processing Record 6- atuona
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=atuona
    Processing Record 7- yeppoon
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yeppoon
    Processing Record 8- punta arenas
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=punta arenas
    Processing Record 9- khatanga
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=khatanga
    Processing Record 10- mataura
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mataura
    Processing Record 11- san onofre
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=san onofre
    Processing Record 12- provideniya
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=provideniya
    Processing Record 13- upernavik
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=upernavik
    Processing Record 14- neryungri
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=neryungri
    Processing Record 15- limon
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=limon
    Processing Record 16- tingi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tingi
    Processing Record 17- rikitea
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rikitea
    Processing Record 18- havre-saint-pierre
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=havre-saint-pierre
    Processing Record 19- ariquemes
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ariquemes
    Processing Record 20- rentina
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rentina
    Processing Record 21- ushuaia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ushuaia
    Processing Record 22- paamiut
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=paamiut
    Processing Record 23- cape town
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cape town
    Processing Record 24- cairns
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cairns
    Processing Record 25- saint-philippe
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=saint-philippe
    Processing Record 26- yar-sale
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yar-sale
    Processing Record 27- kavieng
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kavieng
    Processing Record 28- clyde river
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=clyde river
    Processing Record 29- busselton
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=busselton
    Processing Record 30- biak
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=biak
    Processing Record 31- nanortalik
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nanortalik
    Processing Record 32- east london
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=east london
    Processing Record 33- jamestown
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=jamestown
    Processing Record 34- port shepstone
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=port shepstone
    Processing Record 35- the valley
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=the valley
    Processing Record 36- road town
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=road town
    Processing Record 37- kapaa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kapaa
    Processing Record 38- ostrovnoy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ostrovnoy
    Processing Record 39- hami
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hami
    Processing Record 40- thompson
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=thompson
    Processing Record 41- totness
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=totness
    Processing Record 42- hamilton
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hamilton
    Processing Record 43- hambantota
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hambantota
    Processing Record 44- tashtyp
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tashtyp
    Processing Record 45- victoria
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=victoria
    Processing Record 46- tasiilaq
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tasiilaq
    Processing Record 47- sao gabriel da cachoeira
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sao gabriel da cachoeira
    Processing Record 48- hasaki
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hasaki
    Processing Record 49- pangkalanbuun
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pangkalanbuun
    Processing Record 50- lagoa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lagoa
    Processing Record 51- ponta do sol
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ponta do sol
    Processing Record 52- butaritari
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=butaritari
    Processing Record 53- nushki
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nushki
    Processing Record 54- nikolskoye
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nikolskoye
    Processing Record 55- chhindwara
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=chhindwara
    Processing Record 56- taybad
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=taybad
    Processing Record 57- maldonado
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=maldonado
    Processing Record 58- mosquera
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mosquera
    Processing Record 59- charters towers
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=charters towers
    Processing Record 60- iqaluit
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=iqaluit
    Processing Record 61- saldanha
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=saldanha
    Processing Record 62- bambous virieux
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bambous virieux
    Processing Record 63- hermanus
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hermanus
    Processing Record 64- coro
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=coro
    Processing Record 65- barrow
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=barrow
    Processing Record 66- sitka
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sitka
    Processing Record 67- pitimbu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pitimbu
    Processing Record 68- fuyang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=fuyang
    Processing Record 69- quatre cocos
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=quatre cocos
    Processing Record 70- mount isa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mount isa
    Processing Record 71- sao joao da barra
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sao joao da barra
    Processing Record 72- kautokeino
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kautokeino
    Processing Record 73- puerto ayora
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=puerto ayora
    Processing Record 74- mar del plata
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mar del plata
    Processing Record 75- kawalu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kawalu
    Processing Record 76- bethel
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bethel
    Processing Record 77- salalah
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=salalah
    Processing Record 78- lebu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lebu
    Processing Record 79- darhan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=darhan
    Processing Record 80- hobart
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hobart
    Processing Record 81- leningradskiy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=leningradskiy
    Processing Record 82- port alfred
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=port alfred
    Processing Record 83- havoysund
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=havoysund
    Processing Record 84- new norfolk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=new norfolk
    Processing Record 85- mugur-aksy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mugur-aksy
    Processing Record 86- camacupa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=camacupa
    Processing Record 87- soria
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=soria
    Processing Record 88- severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=severo-kurilsk
    Processing Record 89- avarua
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=avarua
    Processing Record 90- almaznyy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=almaznyy
    Processing Record 91- hilo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hilo
    Processing Record 92- kahului
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kahului
    Processing Record 93- harpanahalli
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=harpanahalli
    Processing Record 94- bolobo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bolobo
    Processing Record 95- bluff
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bluff
    Processing Record 96- kruisfontein
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kruisfontein
    Processing Record 97- jalu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=jalu
    Processing Record 98- klaksvik
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=klaksvik
    Processing Record 99- arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=arraial do cabo
    Processing Record 100- sibolga
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sibolga
    Processing Record 101- samarai
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=samarai
    Processing Record 102- juneau
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=juneau
    Processing Record 103- nyurba
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nyurba
    Processing Record 104- sabang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sabang
    Processing Record 105- vardo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vardo
    Processing Record 106- antofagasta
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=antofagasta
    Processing Record 107- gat
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=gat
    Processing Record 108- tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tuktoyaktuk
    Processing Record 109- berdigestyakh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=berdigestyakh
    Processing Record 110- kourou
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kourou
    Processing Record 111- longyearbyen
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=longyearbyen
    Processing Record 112- port hueneme
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=port hueneme
    Processing Record 113- saint anthony
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=saint anthony
    Processing Record 114- isangel
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=isangel
    Processing Record 115- ferreira do alentejo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ferreira do alentejo
    Processing Record 116- fairbanks
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=fairbanks
    Processing Record 117- gladstone
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=gladstone
    Processing Record 118- poum
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=poum
    Processing Record 119- talnakh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=talnakh
    Processing Record 120- klyuchi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=klyuchi
    Processing Record 121- haines junction
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=haines junction
    Processing Record 122- barranca
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=barranca
    Processing Record 123- pevek
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pevek
    Processing Record 124- mount gambier
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mount gambier
    Processing Record 125- banda aceh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=banda aceh
    Processing Record 126- evensk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=evensk
    Processing Record 127- svetlogorsk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=svetlogorsk
    Processing Record 128- vista hermosa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vista hermosa
    Processing Record 129- kavaratti
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kavaratti
    Processing Record 130- novyy urengoy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=novyy urengoy
    Processing Record 131- albany
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=albany
    Processing Record 132- lincoln
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lincoln
    Processing Record 133- hermiston
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hermiston
    Processing Record 134- mahasamund
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mahasamund
    Processing Record 135- la ronge
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=la ronge
    Processing Record 136- kawhia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kawhia
    Processing Record 137- luderitz
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=luderitz
    Processing Record 138- kamaishi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kamaishi
    Processing Record 139- umm bab
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=umm bab
    Processing Record 140- adrar
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=adrar
    Processing Record 141- mana
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mana
    Processing Record 142- namibe
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=namibe
    Processing Record 143- bredasdorp
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bredasdorp
    Processing Record 144- tuatapere
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tuatapere
    Processing Record 145- kodiak
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kodiak
    Processing Record 146- lompoc
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lompoc
    Processing Record 147- chipinge
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=chipinge
    Processing Record 148- broome
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=broome
    Processing Record 149- loandjili
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=loandjili
    Processing Record 150- padang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=padang
    Processing Record 151- georgetown
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=georgetown
    Processing Record 152- soyo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=soyo
    Processing Record 153- marsa matruh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=marsa matruh
    Processing Record 154- taoudenni
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=taoudenni
    Processing Record 155- heyang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=heyang
    Processing Record 156- cidreira
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cidreira
    Processing Record 157- inhambane
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=inhambane
    Processing Record 158- kiama
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kiama
    Processing Record 159- lakatoro
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lakatoro
    Processing Record 160- aleksandrov gay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=aleksandrov gay
    Processing Record 161- cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cabo san lucas
    Processing Record 162- nongpoh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nongpoh
    Processing Record 163- ormara
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ormara
    Processing Record 164- hokitika
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hokitika
    Processing Record 165- ribeira grande
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ribeira grande
    Processing Record 166- qaanaaq
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=qaanaaq
    Processing Record 167- castro
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=castro
    Processing Record 168- souillac
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=souillac
    Processing Record 169- yellowknife
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yellowknife
    Processing Record 170- norsup
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=norsup
    Processing Record 171- palmer
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=palmer
    Processing Record 172- novoagansk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=novoagansk
    Processing Record 173- sinnamary
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sinnamary
    Processing Record 174- punta gorda
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=punta gorda
    Processing Record 175- saskylakh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=saskylakh
    Processing Record 176- sembakung
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sembakung
    Processing Record 177- mataram
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mataram
    Processing Record 178- bafq
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bafq
    Processing Record 179- san luis
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=san luis
    Processing Record 180- tallahassee
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tallahassee
    Processing Record 181- meulaboh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=meulaboh
    Processing Record 182- tynset
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tynset
    Processing Record 183- saint george
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=saint george
    Processing Record 184- mayumba
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mayumba
    Processing Record 185- jumla
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=jumla
    Processing Record 186- garmsar
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=garmsar
    Processing Record 187- coahuayana
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=coahuayana
    Processing Record 188- guerrero negro
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=guerrero negro
    Processing Record 189- chokurdakh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=chokurdakh
    Processing Record 190- champerico
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=champerico
    Processing Record 191- grindavik
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=grindavik
    Processing Record 192- marsabit
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=marsabit
    Processing Record 193- dingzhou
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dingzhou
    Processing Record 194- topeka
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=topeka
    Processing Record 195- wanning
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=wanning
    Processing Record 196- kukmor
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kukmor
    Processing Record 197- nosy varika
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nosy varika
    Processing Record 198- dunedin
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dunedin
    Processing Record 199- taicheng
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=taicheng
    Processing Record 200- concordia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=concordia
    Processing Record 201- huarmey
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=huarmey
    Processing Record 202- tocache
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tocache
    Processing Record 203- pathardi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pathardi
    Processing Record 204- panaba
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=panaba
    Processing Record 205- mitsamiouli
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mitsamiouli
    Processing Record 206- manado
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=manado
    Processing Record 207- faanui
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=faanui
    Processing Record 208- nalut
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nalut
    Processing Record 209- sao felix do xingu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sao felix do xingu
    Processing Record 210- cap malheureux
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cap malheureux
    Processing Record 211- minot
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=minot
    Processing Record 212- kieta
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kieta
    Processing Record 213- mvuma
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mvuma
    Processing Record 214- tabou
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tabou
    Processing Record 215- rio branco
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rio branco
    Processing Record 216- spas
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=spas
    Processing Record 217- roald
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=roald
    Processing Record 218- kijang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kijang
    Processing Record 219- ulkan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ulkan
    Processing Record 220- avera
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=avera
    Processing Record 221- la rioja
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=la rioja
    Processing Record 222- kurdzhinovo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kurdzhinovo
    Processing Record 223- ilulissat
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ilulissat
    Processing Record 224- bandipur
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bandipur
    Processing Record 225- bhaderwah
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bhaderwah
    Processing Record 226- touros
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=touros
    Processing Record 227- lorengau
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lorengau
    Processing Record 228- tommot
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tommot
    Processing Record 229- umm kaddadah
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=umm kaddadah
    Processing Record 230- chilliwack
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=chilliwack
    Processing Record 231- san jeronimo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=san jeronimo
    Processing Record 232- dudinka
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dudinka
    Processing Record 233- hithadhoo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hithadhoo
    Processing Record 234- kaitangata
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kaitangata
    Processing Record 235- torbay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=torbay
    Processing Record 236- mogok
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mogok
    Processing Record 237- chuy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=chuy
    Processing Record 238- huejuquilla el alto
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=huejuquilla el alto
    Processing Record 239- kudahuvadhoo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kudahuvadhoo
    Processing Record 240- primo tapia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=primo tapia
    Processing Record 241- glendive
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=glendive
    Processing Record 242- srirampur
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=srirampur
    Processing Record 243- gandorhun
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=gandorhun
    Processing Record 244- kyren
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kyren
    Processing Record 245- sao jose da coroa grande
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sao jose da coroa grande
    Processing Record 246- mirabad
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mirabad
    Processing Record 247- airai
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=airai
    Processing Record 248- mariental
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mariental
    Processing Record 249- port elizabeth
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=port elizabeth
    Processing Record 250- policoro
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=policoro
    Processing Record 251- port hardy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=port hardy
    Processing Record 252- hualmay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hualmay
    Processing Record 253- yeniseysk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yeniseysk
    Processing Record 254- kaeo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kaeo
    Processing Record 255- zhigansk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=zhigansk
    Processing Record 256- pedernales
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pedernales
    Processing Record 257- george
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=george
    Processing Record 258- igarka
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=igarka
    Processing Record 259- tongliao
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tongliao
    Processing Record 260- mahebourg
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mahebourg
    Processing Record 261- praia da vitoria
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=praia da vitoria
    Processing Record 262- prince rupert
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=prince rupert
    Processing Record 263- oranjemund
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=oranjemund
    Processing Record 264- paharpur
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=paharpur
    Processing Record 265- itapeva
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=itapeva
    Processing Record 266- copperas cove
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=copperas cove
    Processing Record 267- lata
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lata
    Processing Record 268- shakawe
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=shakawe
    Processing Record 269- los llanos de aridane
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=los llanos de aridane
    Processing Record 270- mogwase
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mogwase
    Processing Record 271- galle
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=galle
    Processing Record 272- general bravo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=general bravo
    Processing Record 273- agnibilekrou
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=agnibilekrou
    Processing Record 274- sobolevo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sobolevo
    Processing Record 275- bubaque
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bubaque
    Processing Record 276- roma
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=roma
    Processing Record 277- tomari
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tomari
    Processing Record 278- vila velha
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vila velha
    Processing Record 279- muros
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=muros
    Processing Record 280- dalbandin
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dalbandin
    Processing Record 281- pontianak
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pontianak
    Processing Record 282- lanzhou
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lanzhou
    Processing Record 283- makkaveyevo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=makkaveyevo
    Processing Record 284- changji
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=changji
    Processing Record 285- espinosa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=espinosa
    Processing Record 286- khorramshahr
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=khorramshahr
    Processing Record 287- husavik
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=husavik
    Processing Record 288- mareeba
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mareeba
    Processing Record 289- neiafu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=neiafu
    Processing Record 290- kongolo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kongolo
    Processing Record 291- katsuura
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=katsuura
    Processing Record 292- tiksi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tiksi
    Processing Record 293- richards bay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=richards bay
    Processing Record 294- ahraura
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ahraura
    Processing Record 295- russkiy aktash
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=russkiy aktash
    Processing Record 296- kurilsk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kurilsk
    Processing Record 297- heihe
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=heihe
    Processing Record 298- pisco
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pisco
    Processing Record 299- matara
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=matara
    Processing Record 300- bathsheba
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bathsheba
    Processing Record 301- carauari
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=carauari
    Processing Record 302- aykhal
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=aykhal
    Processing Record 303- srednekolymsk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=srednekolymsk
    Processing Record 304- moratuwa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=moratuwa
    Processing Record 305- ankang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ankang
    Processing Record 306- kutum
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kutum
    Processing Record 307- lappeenranta
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lappeenranta
    Processing Record 308- broken hill
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=broken hill
    Processing Record 309- general roca
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=general roca
    Processing Record 310- balabac
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=balabac
    Processing Record 311- siderno
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=siderno
    Processing Record 312- comodoro rivadavia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=comodoro rivadavia
    Processing Record 313- podosinovets
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=podosinovets
    Processing Record 314- constitucion
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=constitucion
    Processing Record 315- qaqortoq
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=qaqortoq
    Processing Record 316- manvi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=manvi
    Processing Record 317- kande
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kande
    Processing Record 318- marzuq
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=marzuq
    Processing Record 319- komsomolskiy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=komsomolskiy
    Processing Record 320- hillsboro
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hillsboro
    Processing Record 321- palora
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=palora
    Processing Record 322- marfino
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=marfino
    Processing Record 323- luanda
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=luanda
    Processing Record 324- louis trichardt
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=louis trichardt
    Processing Record 325- black river
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=black river
    Processing Record 326- purranque
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=purranque
    Processing Record 327- tolaga bay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tolaga bay
    Processing Record 328- puri
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=puri
    Processing Record 329- narsaq
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=narsaq
    Processing Record 330- iquique
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=iquique
    Processing Record 331- mildmay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mildmay
    Processing Record 332- labuhan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=labuhan
    Processing Record 333- merauke
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=merauke
    Processing Record 334- sorland
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sorland
    Processing Record 335- owensboro
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=owensboro
    Processing Record 336- kota tinggi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kota tinggi
    Processing Record 337- kimberley
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kimberley
    Processing Record 338- demmin
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=demmin
    Processing Record 339- panama city
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=panama city
    Processing Record 340- belaya gora
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=belaya gora
    Processing Record 341- kapit
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kapit
    Processing Record 342- lavrentiya
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lavrentiya
    Processing Record 343- idrija
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=idrija
    Processing Record 344- pringsewu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pringsewu
    Processing Record 345- sistranda
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sistranda
    Processing Record 346- mogadishu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mogadishu
    Processing Record 347- yulara
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yulara
    Processing Record 348- ancud
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ancud
    Processing Record 349- araouane
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=araouane
    Processing Record 350- colonial heights
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=colonial heights
    Processing Record 351- hobyo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hobyo
    Processing Record 352- oyama
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=oyama
    Processing Record 353- wum
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=wum
    Processing Record 354- kangaba
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kangaba
    Processing Record 355- karwar
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=karwar
    Processing Record 356- panzhihua
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=panzhihua
    Processing Record 357- kaoma
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kaoma
    Processing Record 358- randazzo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=randazzo
    Processing Record 359- cherskiy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cherskiy
    Processing Record 360- baykit
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=baykit
    Processing Record 361- luganville
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=luganville
    Processing Record 362- buriti
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=buriti
    Processing Record 363- wentzville
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=wentzville
    Processing Record 364- ordzhonikidze
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ordzhonikidze
    Processing Record 365- khorixas
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=khorixas
    Processing Record 366- rio gallegos
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rio gallegos
    Processing Record 367- challapata
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=challapata
    Processing Record 368- dingle
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dingle
    Processing Record 369- nazca
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nazca
    Processing Record 370- bastia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bastia
    Processing Record 371- beringovskiy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=beringovskiy
    Processing Record 372- waingapu
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=waingapu
    Processing Record 373- geraldton
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=geraldton
    Processing Record 374- aasiaat
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=aasiaat
    Processing Record 375- khani
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=khani
    Processing Record 376- rockhampton
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rockhampton
    Processing Record 377- port blair
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=port blair
    Processing Record 378- shiyan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=shiyan
    Processing Record 379- talcahuano
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=talcahuano
    Processing Record 380- joson
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=joson
    Processing Record 381- acapulco
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=acapulco
    Processing Record 382- tamworth
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tamworth
    Processing Record 383- cockburn town
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cockburn town
    Processing Record 384- mackay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mackay
    Processing Record 385- batagay-alyta
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=batagay-alyta
    Processing Record 386- amapa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=amapa
    Processing Record 387- jinchang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=jinchang
    Processing Record 388- nanchang
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=nanchang
    Processing Record 389- brigantine
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=brigantine
    Processing Record 390- naze
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=naze
    Processing Record 391- ternate
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ternate
    Processing Record 392- ketchikan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ketchikan
    Processing Record 393- vila
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vila
    Processing Record 394- hay river
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hay river
    Processing Record 395- vanimo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vanimo
    Processing Record 396- conceicao do araguaia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=conceicao do araguaia
    Processing Record 397- sabancuy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sabancuy
    Processing Record 398- shimoda
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=shimoda
    Processing Record 399- knysna
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=knysna
    Processing Record 400- temyasovo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=temyasovo
    Processing Record 401- pacifica
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pacifica
    Processing Record 402- eyl
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=eyl
    Processing Record 403- jieshi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=jieshi
    Processing Record 404- trapani
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=trapani
    Processing Record 405- chulym
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=chulym
    Processing Record 406- mbuji-mayi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mbuji-mayi
    Processing Record 407- sivaki
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sivaki
    Processing Record 408- dryden
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dryden
    Processing Record 409- bloemfontein
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bloemfontein
    Processing Record 410- karratha
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=karratha
    Processing Record 411- hornepayne
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=hornepayne
    Processing Record 412- leh
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=leh
    Processing Record 413- concarneau
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=concarneau
    Processing Record 414- rincon
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rincon
    Processing Record 415- jimenez
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=jimenez
    Processing Record 416- tura
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tura
    Processing Record 417- fort nelson
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=fort nelson
    Processing Record 418- calamar
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=calamar
    Processing Record 419- muravlenko
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=muravlenko
    Processing Record 420- homer
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=homer
    Processing Record 421- krasnyy bogatyr
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=krasnyy bogatyr
    Processing Record 422- te anau
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=te anau
    Processing Record 423- omboue
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=omboue
    Processing Record 424- gizo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=gizo
    Processing Record 425- marshall
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=marshall
    Processing Record 426- keti bandar
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=keti bandar
    Processing Record 427- roebourne
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=roebourne
    Processing Record 428- praia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=praia
    Processing Record 429- bien hoa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bien hoa
    Processing Record 430- aklavik
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=aklavik
    Processing Record 431- atar
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=atar
    Processing Record 432- damavand
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=damavand
    Processing Record 433- vagur
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vagur
    Processing Record 434- pitiquito
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pitiquito
    Processing Record 435- osinovo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=osinovo
    Processing Record 436- thunder bay
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=thunder bay
    Processing Record 437- honiara
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=honiara
    Processing Record 438- mtwango
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mtwango
    Processing Record 439- norman wells
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=norman wells
    Processing Record 440- tokur
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=tokur
    Processing Record 441- liwale
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=liwale
    Processing Record 442- maragogi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=maragogi
    Processing Record 443- brody
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=brody
    Processing Record 444- sovetskaya gavan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sovetskaya gavan
    Processing Record 445- smolenka
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=smolenka
    Processing Record 446- aripuana
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=aripuana
    Processing Record 447- lakeside
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=lakeside
    Processing Record 448- vikulovo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=vikulovo
    Processing Record 449- shaunavon
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=shaunavon
    Processing Record 450- verkhnevilyuysk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=verkhnevilyuysk
    Processing Record 451- yumen
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yumen
    Processing Record 452- sechura
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=sechura
    Processing Record 453- gravdal
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=gravdal
    Processing Record 454- erdenet
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=erdenet
    Processing Record 455- orchard homes
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=orchard homes
    Processing Record 456- flinders
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=flinders
    Processing Record 457- chingirlau
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=chingirlau
    Processing Record 458- deputatskiy
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=deputatskiy
    Processing Record 459- rio grande
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rio grande
    Processing Record 460- villa del rosario
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=villa del rosario
    Processing Record 461- talavera de la reina
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=talavera de la reina
    Processing Record 462- bindura
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bindura
    Processing Record 463- pangoa
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=pangoa
    Processing Record 464- skibbereen
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=skibbereen
    Processing Record 465- dromolaxia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=dromolaxia
    Processing Record 466- aswan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=aswan
    Processing Record 467- artesia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=artesia
    Processing Record 468- rudsar
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=rudsar
    Processing Record 469- whyalla
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=whyalla
    Processing Record 470- cayenne
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=cayenne
    Processing Record 471- faya
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=faya
    Processing Record 472- corning
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=corning
    Processing Record 473- bochil
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=bochil
    Processing Record 474- manzanillo
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=manzanillo
    Processing Record 475- miranda
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=miranda
    Processing Record 476- monrovia
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=monrovia
    Processing Record 477- am timan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=am timan
    Processing Record 478- gibara
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=gibara
    Processing Record 479- biltine
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=biltine
    Processing Record 480- diamantino
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=diamantino
    Processing Record 481- eureka
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=eureka
    Processing Record 482- yate
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yate
    Processing Record 483- kuytun
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=kuytun
    Processing Record 484- solwezi
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=solwezi
    Processing Record 485- yatou
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=yatou
    Processing Record 486- san andres
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=san andres
    Processing Record 487- laizhou
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=laizhou
    Processing Record 488- okhotsk
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=okhotsk
    Processing Record 489- esperance
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=esperance
    Processing Record 490- goundam
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=goundam
    Processing Record 491- zonguldak
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=zonguldak
    Processing Record 492- itarema
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=itarema
    Processing Record 493- ust-kulom
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ust-kulom
    Processing Record 494- raudeberg
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=raudeberg
    Processing Record 495- mahina
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=mahina
    Processing Record 496- buncrana
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=buncrana
    Processing Record 497- necochea
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=necochea
    Processing Record 498- taguatinga
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=taguatinga
    Processing Record 499- ligayan
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=ligayan
    Processing Record 500- fortuna
    http://api.openweathermap.org/data/2.5/weather?appid=0ab5ea923c906feec8511e590cfee362&units=imperial&q=fortuna
    


```python
weather_data = []

for city in cities:
    weather_data.append(req.get(query_url + city).json())
weather_data[0]
```




    {'base': 'stations',
     'clouds': {'all': 56},
     'cod': 200,
     'coord': {'lat': 14.9, 'lon': -24.5},
     'dt': 1519691638,
     'id': 3374210,
     'main': {'grnd_level': 1016.22,
      'humidity': 100,
      'pressure': 1016.22,
      'sea_level': 1028.13,
      'temp': 68.23,
      'temp_max': 68.23,
      'temp_min': 68.23},
     'name': 'Sao Filipe',
     'sys': {'country': 'CV',
      'message': 0.0037,
      'sunrise': 1519718169,
      'sunset': 1519760725},
     'weather': [{'description': 'broken clouds',
       'icon': '04n',
       'id': 803,
       'main': 'Clouds'}],
     'wind': {'deg': 334.501, 'speed': 4.97}}




```python
# Extract interesting data from responses
lat_data = [data.get("coord").get("lat") for data in weather_data]
temperature_data = [data.get("main").get("temp") for data in weather_data]
humidity_data = [data.get("main").get("humidity") for data in weather_data]
cloudy_data = [data.get("clouds").get("all") for data in weather_data]
wind_speed = [data.get("wind").get("speed") for data in weather_data]

weather_data = {"Temperature": temperature_data, "Latitude": lat_data, "Humidity": humidity_data, "Cloudiness": cloudy_data, "Wind Speed": wind_speed}
weather_data = pd.DataFrame(weather_data, index=cities)

weather_data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Cloudiness</th>
      <th>Humidity</th>
      <th>Latitude</th>
      <th>Temperature</th>
      <th>Wind Speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>sao filipe</th>
      <td>56</td>
      <td>100</td>
      <td>14.90</td>
      <td>68.23</td>
      <td>4.97</td>
    </tr>
    <tr>
      <th>carnarvon</th>
      <td>0</td>
      <td>36</td>
      <td>-30.97</td>
      <td>47.98</td>
      <td>2.84</td>
    </tr>
    <tr>
      <th>dikson</th>
      <td>20</td>
      <td>84</td>
      <td>73.51</td>
      <td>-13.18</td>
      <td>16.49</td>
    </tr>
    <tr>
      <th>vaini</th>
      <td>0</td>
      <td>39</td>
      <td>15.34</td>
      <td>58.69</td>
      <td>4.63</td>
    </tr>
    <tr>
      <th>ahipara</th>
      <td>12</td>
      <td>70</td>
      <td>-35.17</td>
      <td>75.21</td>
      <td>5.97</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Export file as a CSV
weather_data.to_csv("Weather_data.csv", header=True)
```


```python
# Build a scatter plot for each data type
plt.scatter(weather_data["Latitude"], weather_data["Temperature"], marker="o")

# Title and label axis
plt.title("Temperature in World Cities")
plt.ylabel("Temperature (F)")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("TemperatureInWorldCities.png")

# Show plot
plt.show()
```


![png](output_9_0.png)



```python
# Build a scatter plot for each data type
plt.scatter(weather_data["Latitude"], weather_data["Humidity"], marker="o")

# Title and label axis
plt.title("Humidity in World Cities")
plt.ylabel("Humidity (%)")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("HumidityInWorldCities.png")

# Show plot
plt.show()
```


![png](output_10_0.png)



```python
# Build a scatter plot for each data type
plt.scatter(weather_data["Latitude"], weather_data["Cloudiness"], marker="o")

# Title and label axis
plt.title("Cloudiness in World Cities")
plt.ylabel("Cloudiness (%)")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("CloudinessInWorldCities.png")

# Show plot
plt.show()
```


![png](output_11_0.png)



```python
# Build a scatter plot for each data type
plt.scatter(weather_data["Latitude"], weather_data["Wind Speed"], marker="o")

# Title and label axis
plt.title("Wind Speed in World Cities")
plt.ylabel("Wind Speed (mph)")
plt.xlabel("Latitude")
plt.grid(True)

# Save the figure
plt.savefig("WindSpeedInWorldCities.png")

# Show plot
plt.show()
```


![png](output_12_0.png)



```python

```

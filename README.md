# Intro-to-Programming
Class Project
def weather_data(query):
   api_key = "79d6d878dd81653a8c260941af6c6383"
   base_url = "http://api.openweathermap.org/data/2.5/weather?"
   complete_url = base_url + "appid=" + api_key + "&" + query
   res=requests.get(complete_url)
   return res.json()

# function to display results
def display_results(weathers,city):
   print("{}'s temperature: {}°C ".format(city,weathers['main']['temp']))
   print("Wind speed: {} m/s".format(weathers['wind']['speed']))
   print("Description: {}".format(weathers['weather'][0]['description']))
   print("Weather: {}".format(weathers['weather'][0]['main']))

# main function
def main():
   city=input('Enter the city:')
   print()
   try:
      query='q='+city
      w_data=weather_data(query)
      display_results(w_data, city)
      print()
   except:
      print('City name not found')

if __name__=='__main__':
   main()

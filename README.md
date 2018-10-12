# Project-Summary

My project is to investigate economics analysis of online shopping based on data mining.    
The investigation is done by data mining from major platforms for online shopping such as taobao.   
Those data are then analysed using machine learning algorithms via python language, generating the most   
predominant factor that affect a customer’s decision when making decisions. The biggest challenge I faced  
in this investigation is that I have never learned to code nor understand the language of python prior to   
this project. Through watching tutorials that Embark provided, I am able to catch up the basics of the python   
language and furthermore understand sophisticated AI algorithms and how to code them. In my opinion, the most   
interesting part of this investigation is realising that data can be gathered everywhere by using a simple code,   
which answer my question of how are data of simillar studies collected. Through this investigation, I have experienced   
how machine learning can be used to perform tasks in seconds that might take years for humans to accomplish, which   
lead me to the realisation that machine learning will be crucial in researches nowadays that involve overwhelming data   
for humans to manage.

Here’s an example of my code.  
```python
def getall(self):

       '''Extract the page’s ID and analyse the page extraction information of each item according to every ID '''

       time.sleep(0.1)

       '''Scroll the page to the bottom to load all items.'''

       for i in range(18):

           js = "window.scrollTo(0,{})".format(i * 500)

           self.driver.execute_script(js)

           time.sleep(0.3)

       # self.driver.save_screenshot("screenshot.png")        # analyse the loaded page        tree = etree.HTML(self.driver.page_source)

       result = tree.xpath("//div[@id='J_goodsList']/ul/li")

       if result:

           for each in result:

               id = each.xpath('@data-sku')[0]

               price = each.cssselect('div.p-price > strong > i')[0].text

               if id not in self.set:

                   try:

                       self.save_info(id, price)

                       self.set.add(id)

                   except Exception as e:

                       print(id, e)



       next_page = tree.xpath("//a[@class='pn-next']")

       if next_page and self.max_p - 1:

           self.max_p -= 1

           self.driver.find_element_by_xpath("//a[@class='pn-next']").click()

           time.sleep(0.1)

           next_url = self.driver.current_url

           pagenum = re.findall("&page=(\d*?)&", next_url)[0]

           pagenum = (int(pagenum) + 1) // 2

           print('find the next page,about to extract information on page {}'.format(pagenum))

           self.getall()

       else:

           print("All pages have been extracted completely!")
```

* Name: 何瀚圻 Hanqi He
* English Name: Hanson
* Gender: Male
* Birthday: 12-6-2001
* School: YK Pao
* Future Major(s): Economics, Psychology
* Interests: Football (soccer)

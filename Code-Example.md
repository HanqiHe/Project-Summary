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

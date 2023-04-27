Topic: #ComputerScience 

---

## Types of content discovery
There are three main ways to discover content in a website

### Manually
#### [[Robots.txt]] & sitemap.xml
These both serve simmilar purposes, however from a CySec perspective `robots.txt` can give us a hint at endpoints the sysadmin doesnt want us to find. `sitemap.xml` on the other hand can give point us to areas of the wesbite that are difficult to navigate too, or possibly list some old pages that are officially no longer used.

#### Favicon
Sometimes when frameworks are used to build a website the favicon is left as the framework default. OWASP host a databse of common framework icons [here](https://wiki.owasp.org/index.php/OWASP_favicon_database).

For example with [this site](https://static-labs.tryhackme.cloud/sites/favicon/) you can see this favicon: ![Favicon](https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico) If you inspect the page source you can find the image on the site is hosted at `/images/favicon.ico/`. You can run the following command to get its hash, which you can cross refrence against the OWASP database
```
eddie@ghost$ curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum
```



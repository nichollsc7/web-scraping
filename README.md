# Web scraping
Examples using Web Scraping

## Amazon 
- code
```js
fetch('https://www.amazon.com/s?k=jeans&ref=nb_sb_noss_1')
.then((response) => response.text())
.then((html) => {
    const page = document.createElement('html')
    page.innerHTML = html
    const products = [...page.querySelectorAll('span > div.rush-component')]
    return products.map((p) => {
       return {
         title: p.querySelector('h2 a span').innerText,
         price: p.querySelector('span.a-offscreen').innerText,
         rank: p.querySelector('div.a-section div span:nth-child(2) a span').innerText
 }
    })
})
.then((data) => console.table(data))
.catch((error)=> console.error(error))
```
- output

| index | title | price | rank |
| --- | --- | --- | --- |
| 0	| "Amazon Essentials Men's Skinny-fit Stretch Jean"	| "$29.50"	| "3,914" |
| 1	| "Ethanol Mens Super Comfy Straight Stretch Knit Jersey Denim Five Pocket Jean" |	"$26.38" |	"774" |
| 2	| "Amazon Essentials Men's Athletic-Fit Stretch Jean"	| "$29.00"	| "3,596" |
| 3	| "Lucky Brand Men's 181 Relaxed Straight Jean X Pants"	| "$76.43"	| "2,043" |
| 4	| "Liuhond Skinny Slim Fashion Men's Ripped Straight Holes Hip Hop Biker Stretchy Jeans"	| "$29.99"	| "939" |
| 5	| "Wrangler Authentics Relaxed Fit Comfort Flex Waist Men's Jean Pants"	| "$25.99"	| "12,004" |
| 6	| "Wrangler Authentics Men's Regular Fit Comfort Flex Waist Jean Pants"	| "$25.99"	| "17,741" |
| 7	| "Lucky Brand Men's 367 Vintage Bootcut Jean X Pants"	| "$56.99"	| "789" |
| 8	| "Amazon Essentials Men's Straight-fit Stretch Jean"	| "$29.50"	| "2,849" |
| 9	| "Leward Men's Ripped Skinny Distressed Destroyed Straight Fit Zipper Jeans with Holes"	| "$29.99"	| "955" |
| 10	| "Lucky Brand Men's 410 Athletic Fit Jean X Pants"	| "$76.21"	| "1,201" |
| 11	| "ETHANOL Mens Straight Stretch Motion Denim Jean"	| "$32.49"	| "122" |

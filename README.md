# Harvest-Herd
A single-page demo storefront for browsing and "buying" Nigerian crops, farm produce and livestock.
Features
Three catalogue sections
Crops (20 items): split into Food (rice, maize, cocoa, beans, yam, etc.) and Fruits (apple, orange, watermelon, garden egg, etc.)
Produce (9 items): eggs, pork, chicken, turkey, lamb, fish, milk, honey, manure
Animals (6 types): cattle, chicken, dog, pig, horse, turkey
Livestock options: click an animal to choose Male, Female or Young. Price adjusts automatically (male ×1.12, young ×0.55, female is the base price).
Basket: add and remove items, quantities are tracked, and a running estimated total is shown in a modal dialog.
Currency toggle: display prices in NGN (₦) or USD ($).
Language selector: 20 languages are listed. Section headings and navigation labels (Market, How it works, Crops, Food, Fruits, Produce, Animals) are translated for most of them; the rest of the page stays in English.
Payment dropdown: NGN, USD, USDT, BTC, ETH, BNB and XRP options (display only).
Responsive layout: three columns on desktop, two on tablet, one on mobile.
Getting started

No installation needed.

Download index.html.
Open it in any modern browser.

To serve it locally instead:

bash
python3 -m http.server 8000
# then visit http://localhost:8000/farm-market.html
Project structure
farm-market.html   # markup, styles (CSS) and logic (vanilla JS) in one file

Inside the file:

Part	Purpose
<style>	Theme via CSS variables (--ink, --green, --bg, ...), grid layout and media queries
rows array	Crop and produce catalogue: [name, emoji, price, unit, group]
stock array	Livestock catalogue: [name, emoji, price, unit]
langs / tr	Language list and the small translation table for headings
render()	Builds the product lists and animal cards
add() / basket()	Basket state, totals and the basket dialog
Customising

Add or change a product. Edit the rows array (crops and produce) or the stock array (animals). Prices are in naira.

js
// name, emoji, price (NGN), unit, group ('food' | 'fruit' | 'produce')
['cassava', '🥔', 900, 'per kg', 'food']

If you add items, update the item counts shown in the column headers (20 items, 9 items, 6 animals), since they are hard-coded in the HTML.

Change the USD rate. The conversion is fixed at ₦1,500 per $1, set in the fmt() function (n/1500).

Change livestock multipliers. In render() and the .buy handler, adjust 1.12 (male) and .55 (young).

Add translations. Add an entry to the tr object in this order: Market, How it works, Crops, Food, Fruits, Produce, Animals.

Restyle. Change the colour variables in :root at the top of the stylesheet.

Known limitations
Prices are indicative estimates only and are hard-coded. The page links to the CBN economic reports and FoodPrices NG for reference.
The USD rate is a fixed constant, not a live exchange rate.
The "Pay with" selection does not affect totals, and crypto prices are not converted.
The basket resets on page refresh (no persistence).
Language support covers only the headings and nav links, not product names or descriptions.

Tech

HTML5, CSS3 (grid, flexbox, custom properties) and vanilla JavaScript, using the native <dialog> element for the basket.

Purr'Coffee POS

A simple point-of-sale (POS) web app for a coffee shop. It runs in the browser from a single file, index.html. There is nothing to install and no server is needed.

Live site: https://markkennethkenet.github.io/kainlab-torresgroup/ (after GitHub Pages is turned on)

Features
Menu with 5 categories: Coffee, Non Coffee, Food, Snack, Dessert
Search bar to find products by name
Small / Large size for drinks (Large costs ₱20 more)
Cart with quantity controls and remove button
Order type: Dine in, Take away, Delivery
Order review screen before payment
Three payment methods:
Cash: number keypad, quick amounts, automatic change, "insufficient cash" warning
QR Payment: simulation
Card: simulation
Digital receipt with a Print button
Transaction history for the current session
Unique reference numbers per day, e.g. TXN-20261007-001
Light and dark mode (follows the device setting)
Works on desktop, tablet and phone
How to use
Open index.html in any modern browser (Chrome, Edge, Firefox, Safari).
Pick a category and tap Add to Cart on the items.
Tap Place an order and check the summary.
Tap Proceed to Payment and choose Cash, QR or Card.
View or print the receipt.
Tap New Transaction for the next customer.
Project structure
kainlab/
├── index.html   # the whole app: HTML + CSS + JavaScript
└── README.md    # this file

Inside index.html the script is split into numbered sections:

#	Section	What it does
1	SETTINGS	Values you may want to change
2	HELPERS	Icons, peso format, dates, popup messages
3	MENU DATA	Products, categories, drawn product images
4	CART	Current order, totals
5	TRANSACTIONS	Reference numbers and sales history
6	PAYMENT	Cash validation
7	RECEIPT	Receipt layout
8	SCREENS	One function per screen
9	ACTIONS	What each button does
10	START	Starts the app
Customizing

Change settings in the CONFIG block at the top of the script:

js
const CONFIG = {
  LARGE_EXTRA: 20,
  MAX_QTY: 20,
  PROCESS_MS: 1600,
  MAX_CASH_DIGITS: 7,
  QUICK_AMOUNTS: [200, 500, 1000],
  TOAST_MS: 2400,
  STORAGE_KEY: "pos_tx"
};

Add or edit a product in the PRODUCTS list:

js
{ id: 11, name: "Mocha", price: 110, cat: "Coffee", sizes: 1, art: "cup",
  layers: [[30, 50, "#f1e2cf"], [50, 88, "#6b4430"]],
  desc: "Espresso with chocolate and milk." }
sizes: 1 gives the item Small / Large options (drinks only).
art picks the drawing: cup, croissant, sandwich, cookie, cake or donut.
cat must match a name in CATS.
Data and limits
QR and Card payments are simulations. No real payment is made and no card data is read or stored.
Only the daily reference counter is saved (in the browser's localStorage).
Transaction history is kept in memory only and clears when the page is refreshed.
Prices are in Philippine pesos (₱).
Deploy with GitHub Pages
Push the repo to GitHub.
Go to Settings → Pages.
Set Source to Deploy from a branch, choose main and / (root), then Save.
After 1 to 2 minutes the site is live at the link above.
Working with branches
powershell
git switch -c update-pos      # create and switch to a new branch
git add .
git commit -m "Describe your change"
git push -u origin update-pos # push the branch to GitHub

When ready, open a Pull Request on GitHub and merge it into main. The live site updates after the merge.

Ideas for later
Save the transaction history so it survives a refresh
Daily sales report
Real QR / card payment integration
Product management screen (add and edit items without touching code)
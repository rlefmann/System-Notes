# Create block quotes in Groff

```
.QS
.B1
This is the text of the quote.
.DS R
- John Doe
.DE
.B2
.QE
```

Explanation:
* The `.B1` and `.B2` macros create a box around the quote
* The `.DS R` and `.DE` macros make the author name aligned to the right


---
title: "APM 1110 - FA 2"
author: "Cainglet, Manalaysay"
output: pdf_output 
---

## 4

Amy and Jane are gambling together. A fair coin is tossed repeatedly. Each time a head comes up, Amy wins two euro from Jane, and each time a tail comes up, Amy loses two euro to Jane.

# Simulates coin toss 100 times (with replacement)

```{r}
tosses <- sample(c("H", "T"), size = 100, replace = TRUE)
```

# Amy wins two euros for head but losses two euros for tail

```{r}
win_lose <- ifelse(tosses == "H", 2, -2)
```

# Determine Amy's current balance after each toss

```{r}
balance <- cumsum(win_lose)

## 4a.
# The number of times that Amy is ahead in these 100 tosses
ahead <- sum(balance > 0)

ahead 
```

## 4b.

# How much Amy has won or lost after 100 tosses

```{r}
total <- balance[100]
 if (total > 0) {
  paste("Amy won €", total)
 } else if (total < 0) {
  paste("Amy lost €", abs(total))
 } else {
  "Amy broke even (€0)"
 }

total
```

# Plot of Amy's Winning

```{r}
plot(balance, type = "o", col = "hotpink",
     main = "Amy's Winnings per Coin Toss",
     xlab = "Toss Number", ylab = "Winnings (€)")
abline(h = 0, lty = 2)
```

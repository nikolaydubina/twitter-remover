# twitter-remover

Open corresponding page and run following in browser console. Inspired by gist[^gist].

## Remove Likes

```javascript
setInterval(() => {
  for (const d of document.querySelectorAll('div[data-testid="unlike"]')) {
    d.click()
  }
  window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

## Remove Retweets

```javascript
setInterval(() => {
  for (const d of document.querySelectorAll('div[data-testid="unretweet"]')) {
    d.click();
    for (const c of document.querySelectorAll('div[data-testid="unretweetConfirm"]')) { c.click(); }
  }
  window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

## Remove Tweets

```javascript
setInterval(() => {
  for (const d of document.querySelectorAll('div[data-testid="caret"]')) {
    d.click();
    for (const c of document.querySelectorAll('div[data-testid="Dropdown"]')) {
      if (c.firstChild.getElementsByTagName('div')[1].firstChild.firstChild.innerText == "Delete") {
        c.firstChild.click();
        for (const e of document.querySelectorAll('div[data-testid="confirmationSheetConfirm"]')) {
          e.click();
        }
			}
    }
  }
  window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

## Remove Replies

```javascript
setInterval(() => {
  for (const d of document.querySelectorAll('div[data-testid="caret"]')) {
    d.click();
    for (const c of document.querySelectorAll('div[data-testid="Dropdown"]')) {
      if (c.firstChild.getElementsByTagName('div')[1].firstChild.firstChild.innerText == "Delete") {
        c.firstChild.click();
        for (const e of document.querySelectorAll('div[data-testid="confirmationSheetConfirm"]')) {
          e.click();
        }
			}
    }
  }
  window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

[^gist]: https://gist.github.com/aymericbeaumet/d1d6799a1b765c3c8bc0b675b1a1547d

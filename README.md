# twitter-remover

## Remove Likes

Open your "likes" page and run following in console

```javascript
setInterval(() => {
  for (const d of document.querySelectorAll('div[data-testid="unlike"]')) {
    d.click()
  }
  window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

## Remove Retweets

Open your "posts" page and run following in console

```javascript
setInterval(() => {
  for (const d of document.querySelectorAll('div[data-testid="unretweet"]')) {
    d.click();
    for (const c of document.querySelectorAll('div[data-testid="unretweetConfirm"]')) { c.click(); }
  }
  window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```


## References

* https://gist.github.com/aymericbeaumet/d1d6799a1b765c3c8bc0b675b1a1547d

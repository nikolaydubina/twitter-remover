# twitter-remover

[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fnikolaydubina%2Ftwitter-remover&count_bg=%23848484&title_bg=%231DA1F2&icon=twitter.svg&icon_color=%23FFFEFE&title=removed&edge_flat=false)](https://hits.seeyoufarm.com)

Open corresponding page and run following in browser console. Inspired by gist[^gist].

### Remove Likes

```javascript
setInterval(() => {
    for (const d of document.querySelectorAll('div[data-testid="unlike"]')) {
        d.click()
    }
    window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

### Remove Retweets

```javascript
setInterval(() => {
    for (const d of document.querySelectorAll('div[data-testid="unretweet"]')) {
        d.click();
        for (const c of document.querySelectorAll('div[data-testid="unretweetConfirm"]')) { c.click(); }
    }
    window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

### Remove Tweets

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

### Remove Replies

```javascript
setInterval(() => {
    for (const d of document.querySelectorAll('[data-testid="caret"]')) {
        d.click();
        for (const c of document.querySelectorAll('[data-testid="Dropdown"]')) {
            if (c.firstChild.innerText == 'Delete') {
                c.firstChild.click()
                setTimeout(() => {
                    for (const e of document.querySelectorAll('[data-testid="confirmationSheetConfirm"]')) {
                        e.click();
                    }
                }, 500)
            }
        }
    }
    window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

### Remove Followers 

```javascript
setInterval(() => {
    for (const d of document.querySelectorAll('div[data-testid="UserCell"]')) {
        const more = d.firstChild.childNodes[1].firstChild.childNodes[1].childNodes[2].firstChild;
        if (!more) {
            continue;
        }
        more.click();
        for (const d of document.querySelectorAll('div[data-testid="removeFollower"]')) {
            d.click();
            for (const d of document.querySelectorAll('div[data-testid="confirmationSheetConfirm"]')) { d.click(); }
        }
    }
    window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

[^gist]: https://gist.github.com/aymericbeaumet/d1d6799a1b765c3c8bc0b675b1a1547d

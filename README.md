# twitter-remover / xAI / Grok remover

[![Hits](https://hits.sh/github.com/nikolaydubina/twitter-remover.svg?view=today-total&label=removed&extraCount=4569&logo=twitter)](https://hits.sh/github.com/nikolaydubina/twitter-remover/)

> [!WARNING]  
> Twitter changes front-end often. The code may not work all the time. If you find bugs, submit an issue or open a PR with fix.

Open corresponding page and run following in browser console. Inspired by gist[^gist].

### Remove Grok Imagine

> [!CAUTION]  
> You still need to remove your eniter Grok / xAI account to (hopefully) remove Imagine that you made.

> [!CAUTION]  
> More, given that Grok, xAI, "Restore Purchases" does not work and there are No Refunds, you will loose your subscription payments (up to 300 USD / month).

`2025-10-13` Grok, xAI do not provide method to delete images thay you uploaded to Grok Imagine (neither in iOS, nor in web). deleting all history of chats does not help. deleting account has 30 days grace period. here is a way to automate "Unfavorite" all in web. there is no certainty that those images will be deleted from their servers, but this is your best bet.

```javascript
setInterval(() => {
    for (const d of document.querySelectorAll('button[aria-label="Unsave"]')) {
        d.click()
    }
    window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

### Remove Likes

```javascript
setInterval(() => {
    for (const d of document.querySelectorAll('button[data-testid="unlike"]')) {
        d.click()
    }
    window.scrollTo(0, document.body.scrollHeight)
}, 1000)
```

### Remove Retweets

```javascript
function sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function deleteReplies() {
    for (const d of document.querySelectorAll('[data-testid="unretweet"]')) {
        d.click();
        await sleep(1000);
        for (const c of document.querySelectorAll('[data-testid="unretweetConfirm"]')) { c.click(); }
    }
}

setInterval(deleteReplies, 5000)
setInterval(window.scrollTo(0, document.body.scrollHeight), 5000)
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
function sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function deleteReplies() {
    for (const d of document.querySelectorAll('[data-testid="caret"]')) {
        d.click();
        await sleep(1000);
        for (const c of document.querySelectorAll('[data-testid="Dropdown"]')) {
            if (c.firstChild.innerText.includes('Delete')) {
                c.firstChild.click();
                await sleep(1000);
                for (const e of document.querySelectorAll('[data-testid="confirmationSheetConfirm"]')) {
                    e.click();
                }
            }
        }
        document.querySelector('[data-testid="primaryColumn"]').click();
    }
}

setInterval(deleteReplies, 5000)
setInterval(window.scrollTo(0, document.body.scrollHeight), 5000)
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

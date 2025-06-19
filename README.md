# How to Create the Bookmarklet

*Create a New Bookmark: In your browser (Chrome, Firefox, etc.), right-click your bookmarks bar and select "Add Page..." or "Add Bookmark..."
*Name: Give it a name like "Export to Lichess"
*URL/Address: Delete whatever is in the URL field (like http://...) and paste the javascript code from the ```bookmarklet.js``` file into it.
*Save the bookmark
*Open a chess.com/game page and click the bookmark

bookmarklet.js duped:
```
javascript:(function(){'use strict';function e(t,o,i=5e3){let l=0;const a=100,n=setInterval(function(){const s=document.querySelector(t);s?(clearInterval(n),o(s)):(l+=a)>=i&&(clearInterval(n),o(null))},a)}console.log("Lichess Export: Starting...");const t=document.querySelector('.icon-font-chess.share.live-game-buttons-button, [data-cy="share-button"], .share-button-component');if(!t)return alert("Lichess Export: Could not find the Share button. Try running this on the game over screen.");t.click(),e("#tab-pgn",function(t){if(!t)return alert("Lichess Export: Could not find the PGN tab in the Share menu.");t.click(),e('.share-menu-content textarea, [data-cy="share-pgn-textarea"]',function(t){let o=t?t.value:null;if(!o){const t=document.querySelector(".share-menu-content [pgn]");t&&(o=t.getAttribute("pgn"))}if(!o)return alert("Lichess Export: Could not extract PGN data. Chess.com may have updated their site.");const i="https://lichess.org/paste?pgn="+encodeURIComponent(o);window.open(i,"_blank");const l=document.querySelector("#share-modal .cc-close-button-component");l&&l.click()})})})();
```

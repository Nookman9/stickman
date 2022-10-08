<html><head>
    <meta charset="utf-8">
    <title>Stickman Hook</title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=0">
		<script src="/adinLoader.js"></script>
    <style>
      html,
      body {
        position: absolute;
        top: 0px;
        left: 0px;
        margin: 0;
        padding: 0;
        border: 0;
        overflow: hidden;
        width: 100%;
        height: 100%;
        background-color: black;
      }
      canvas {
        width: 100%;
      }
    </style>

    <!-- Poki SDK -->
    <script src="poki.js"></script>
  <style type="text/css">@font-face {
  font-family: "JUNEGULL";
  font-style: normal;
  font-weight: 400;
  src: url(fonts/JUNEGULL.ttf) format("truetype");
}

@font-face {
  font-family: "Odin";
  font-style: normal;
  font-weight: 400;
  src: url(fonts/Odin-Rounded-Bold.ttf) format("truetype");
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

body {
  font-family: JUNEGULL;
}

.odin-font-loader {
  font-family: Odin;
  opacity: 0;
}

button,
input[type="button"],
.clickable {
  outline: none;
  pointer-events: all;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -webkit-tap-highlight-color: transparent;
}

button::-moz-focus-inner,
input[type="button"]::-moz-focus-inner {
  border: 0;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -webkit-tap-highlight-color: transparent;
}

.ui {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  text-shadow: rgba(0, 6, 95, 0.5) 0 3px 0;
  pointer-events: none;
}

.button {
  display: block;
  background-color: transparent;
  filter: drop-shadow(0px 5px 0px rgba(0, 6, 95, 0.5));
  font-weight: bold;
  text-shadow: rgba(0, 6, 95, 0.5) 0 3px 0;
  font-family: JUNEGULL;
  cursor: pointer;
  border: none;
}

.play-button {
  background-image: url(images/54e99c08dfada2fdd1e3b94b699360a4-btn_play.png);
  background-size: 178px 80px;
  width: 178px;
  height: 80px;
  padding: 16px 25px 16px 54px;
  color: white;
  font-size: 18px;
  display: inline-block;
  margin: 5px;
}

.continue-button {
  background-image: url(images/8c92b88b23a65aece8ad09c9fb12a398-B_PlayButton.png);
  background-size: 100px 100px;
  width: 100px;
  height: 100px;
  position: absolute;
  margin: auto;
  left: 0;
  right: 0;
  bottom: 10px;
}

.level-progress {
  text-align: center;
  margin-top: 45px;
}

.level-progressbar-container {
  display: inline-block;
  width: 100px;
  height: 15px;
  background-color: #666666;
  box-shadow: rgba(0, 6, 95, 0.5) 0 3px 0;
}

.level-progressbar {
  height: 100%;
  background-color: #ffffff;
}

.level-progress .lvl {
  width: 50px;
  display: inline-block;
  color: white;
  font-weight: bold;
}

.level-progress .lvl.current {
  text-align: right;
  padding-right: 10px;
}

.level-progress .lvl.next {
  text-align: left;
  padding-left: 10px;
}

.title {
  width: 80%;
  max-width: 500px;
  display: block;
  margin: auto;
  margin-top: 50px;
  filter: drop-shadow(0px 7px 0px rgba(0, 6, 95, 0.5));
}

.level-cleared {
  text-align: center;
  color: white;
  margin-top: 25px;
  font-size: 1.5em;
}

.pause-button {
  width: 30px;
  height: 30px;
  background-image: url(data:image/png;base64,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);
  background-size: 30px 30px;
  position: absolute;
  left: 10px;
  top: 10px;
}

.back-button {
  background-image: url(images/8c92b88b23a65aece8ad09c9fb12a398-B_PlayButton.png);
  transform: rotateZ(-90deg);
  width: 30px;
  height: 30px;
  background-size: 30px 30px;
  position: absolute;
  left: 10px;
  top: 10px;
  filter: drop-shadow(-5px 0px 0px rgba(0, 6, 95, 0.5));
}

.shop-button {
  width: 80px;
  height: 80px;
  color: #0171a3;
  font-size: 14px;
  display: inline-block;
  margin: 5px;
  text-shadow: none;
  background-image: url(data:image/png;base64,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);
  background-size: 80px 80px;
  position: relative;
}

.shop-button.selected {
  background-image: url(data:image/png;base64,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);
}

.shop-button.locked {
  color: white;
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAM8AAADPCAYAAABSgYVfAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAOZSURBVHhe7drLceJAFEBRM3k6CEfiIBwoU0zBVPnDR1ctGcQ5G7EQDQtdvUb2CwCsanc8rm739rE/voSb7d9ff+2a/WqVLyIU1rB2WIt8mFj4bWuENPQDRMO9WTKiIQuLhnu3RESzFxQOj2RkRLMWEg6PaFRAaRHR8OhGBDR5AeGwFXMDmvRm4bA1cwK6+Y3CYatqQH+OR3hadTDcVNzoqTPqaQfPZ8kd0NTr8urJo76sYFjKyKCmXKcXT5z7pQTD2kaEdOt1u1g8wuE3rXHjP3tC/XDRcC+WvvkPjUc43KOlBsGPj6rnjjy4J0vd1If9ncfUYWuuDZFv8diusUVLXKP+w4CnMTqg2fGYOmzZpZ3Yp3g8KGDrRt7sbdsgmhWPLRvPzOTh6Yy66YsHrjj3LEA8EP2PZ+qTNr93eHYmD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EO2Ox5fd28f++BL4Yv/++r+VE5MHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IxAOReCASD0TigUg8EIkHIvFAJB6IdsfjP7u3j/3xJXC0f3/91MmJyQOReCASD0TigQvO/d45+BTPpROBz0weiMQDZ1zbiX2Lx9YNbmPywA9uGSI/xmP6wHUmD3xx6/A4G4/pA5ddDcQ/i/JMpgwN2zY4mrrbuhqP7Rv87OYwbN/YsjIkJr1BQGxR3V1Nr01AbMicnyWtOAGxAXN/z897s4h4UCMehM1fQEA8mBHhHAxZ5EBE3LtR0ZwMXexARNyb0dGcLLLogYj4bUtFc7Lo4idCYk1LR3Oyyod8JSZGWisWAAAAgCteXv4C/ujMgms5yHkAAAAASUVORK5CYII=);
}

.shop-button.type-rewarded.locked {
  background-image: url(images/71b76f184e6da03830b954235e33ae9c-ShopRewarded.png);
}

.shop-button.type-rewarded.locked.loading,
.shop-button.type-rewarded.locked.disabled {
  background-image: url(images/081cbab0a3ae7cc413d3a7b6f0de1d27-ShopRewardedLoading.png);
}

.shop-button > .load-icon {
  position: absolute;
  width: 20px;
  height: 20px;
  top: 7px;
  right: 7px;
  animation-name: spin;
  animation-duration: 1s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

.shop-button > .text {
  position: absolute;
  top: 55px;
  left: 6px;
  right: 6px;
  bottom: 4px;
}

.shop-button > .image {
  width: 80px;
  position: absolute;
  top: -6px;
  left: 0;
}

.shop-button > .lock {
  position: absolute;
  top: 6px;
  left: 6px;
  width: 16px;
  height: 16px;
}

.shop-button.type-rewarded.locked > .text,
.shop-button.type-rewarded.locked > .lock {
  display: none;
}

.row {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 15px 0;
}

.title-buttons {
  position: absolute;
  bottom: 50px;
  left: 0;
  right: 0;
}

.title-buttons .button {
  margin: 5px;
}

.shop-content {
  background-image: url(data:image/png;base64,/9j/4AAQSkZJRgABAQEASABIAAD/4QAiRXhpZgAATU0AKgAAAAgAAQESAAMAAAABAAEAAAAAAAD/2wBDAAIBAQIBAQICAgICAgICAwUDAwMDAwYEBAMFBwYHBwcGBwcICQsJCAgKCAcHCg0KCgsMDAwMBwkODw0MDgsMDAz/2wBDAQICAgMDAwYDAwYMCAcIDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAz/wAARCAUAAAEDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwDPooor+lD+WwooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKAH7BRS0VnzGdwxRUmKKzAkooorO4DvLop2KKz5iSSinbKKzJDb70VJ5dFZ3AdRRRWYEmKKd5dFZ8wuVDqKkorMNQoqTFFZ3IuO2UU6is+YAoqTFFZXQDtlFOoqBWF2Gin0VF2Go/YKKWiseYi4uw0U/FFRcCSiiiswHeXRTsUVnzE6klFLsNFY8wXH0U7y6Km4rsdRRRWYiTFFO8uis+YB1FO2UVjzE6jqKkxRU3JHbKKdRWdx3YUVJiiseYQ/YKKWipuAuw0U+isronUfsFFLRWXMTckooxRWfMVzElFFFZ8xI7ZRTsUVF0BJRRRWXMTzElFO8uis+Ym46ipKKz5gCineXRWfMA6inbKKyuwHUVJiio5ieYdsop1FZXZIUVJiio5gH7BRSbKKz5gH7DRT6Kz5ieYfsFFLRWNw5hdhop+KKzuSf/Z);
  background-size: 100% 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  top: 33%;
}

.skins-lists-container {
  position: relative;
  height: calc(100% - 68px);
  left: 0%;
  transition: ease 0.5s;
}

.skins-list {
  text-align: center;
  overflow: auto;
  height: 100%;
  display: inline-block;
}

.shop-progress {
  position: absolute;
  top: 10px;
  right: 10px;
  color: white;
  font-size: 20px;
}

.shop .shop-button {
  text-shadow: none;
}

.shop-category-name {
  background-color: white;
  color: #00b9dc;
  text-align: center;
  text-shadow: none;
  padding: 5px;
  line-height: 25px;
}

.shop-category-name > span {
  width: 200px;
  display: inline-block;
}

.clicked-skin-info {
  color: white;
  background-color: #00b9dc;
  text-align: center;
  padding: 5px;
  filter: drop-shadow(0px 3px 0px rgba(0, 6, 95, 0.5));
  margin-bottom: 10px;
}

.red-arrow {
  cursor: pointer;
  width: 25px;
  vertical-align: middle;
}

.red-arrow.orientation-left {
  transform: scaleX(-1);
}

.red-arrow.disabled {
  opacity: 0.5;
}

.level-debug-infos {
  font-size: 10px;
  font-family: Arial, Helvetica, sans-serif;
  text-shadow: none;
  position: absolute;
  left: 0;
  bottom: 0;
}

.popup-container {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 6, 95, 0.5);
}

.popup-container > div {
  position: absolute;
  top: 0;
  bottom: 50px;
  left: 0;
  right: 0;
}

.skin-unlocked-popup {
  color: white;
  border: 10px solid white;
  border-radius: 4px;
  width: 250px;
  height: 250px;
  text-align: center;
  position: absolute;
  margin: auto;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  overflow: hidden;
}

.skin-unlocked-popup::before {
  content: "";
  position: absolute;
  width: 200%;
  height: 200%;
  top: -50%;
  left: -50%;
  z-index: -1;
  background-color: #438dbe;
  background-image: url(images/93ff3fc5d168e31f731739824e0659b3-SHOP_UI0005.png);
  background-position: 50% 50%;
  animation-name: spin;
  animation-duration: 5s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

.skin-unlocked-popup img {
  width: 200px;
  height: 200px;
  margin-top: 25px;
}

.skin-unlocked-popup > p {
  text-shadow: rgba(0, 6, 95, 0.5) 0 2px 0;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
}

.skin-unlocked-popup .equip-skin-button {
  background-color: #0171a3;
  padding: 7px 12px;
  border-radius: 15px;
  border: 4px solid #00b9dc;
  color: white;
  filter: none;
  text-shadow: rgba(0, 6, 95, 0.5) 0 2px 0;
  margin: auto;
  position: absolute;
  bottom: 10px;
  left: 0;
  right: 0;
  width: 125px;
}

.share-button {
  color: white;
  padding: 9px 12px;
  font-size: 18px;
  font-weight: normal;
  width: 100px;
  height: 50px;
  background-image: url(images/9fbf958a795fda3dfcc89826130fcad7-btn_share.png);
  background-size: 100px 50px;
}

.victory {
  margin: auto;
  width: 300px;
}

.victory .shop-button {
  position: absolute;
  bottom: 15px;
  right: 4%;
}

.victory .share-button {
  position: absolute;
  bottom: 125px;
  left: 4%;
  font-size: 12px;
}

.leaderboard-button {
  color: white;
  padding: 10px 20px;
  font-size: 12px;
  font-weight: normal;
  width: 123px;
  height: 50px;
  background-image: url(images/7d2f8caa50780cb5b5d660370723475e-btn_leaderboard.png);
  background-size: 123px 50px;
}

.victory .leaderboard-button {
  position: absolute;
  bottom: 65px;
  left: 4%;
  width: 100px;
  height: 50px;
  background-size: 100px 50px;
  font-size: 10px;
  padding: 10px 10px;
}

.leaderboard {
  height: 100%;
  overflow: auto;
  pointer-events: all;
  color: white;
}

.leaderboard h2,
.leaderboard h3 {
  text-align: center;
}

.leaderboard .leaderboard-button {
  display: inline-block;
  margin: 0 5px 15px;
}

.leaderboard-entries {
  display: table;
  width: 100%;
  border-collapse: separate;
  border-spacing: 0 5px;
}

.leaderboard-row {
  display: table-row;
  background-color: rgba(0, 6, 95, 0.5);
}

.leaderboard-row.current {
  background-color: rgba(86, 255, 128, 0.5);
}

.leaderboard-col {
  display: table-cell;
  vertical-align: middle;
  padding: 5px;
}

.leaderboard-col.photo,
.leaderboard-col.photo img {
  width: 50px;
  height: 50px;
}

.leaderboard-col.photo img {
  display: block;
  word-break: break-word;
}

.pagination {
  text-align: center;
}

.pagination .page-number {
  display: inline-block;
  width: 200px;
  margin: 20px 0;
}

.center {
  text-align: center;
}

.loading-ui {
  color: white;
  text-align: center;
  height: 100%;
  margin: 0;
}

.loading-ui > img {
  text-align: center;
  position: absolute;
  margin: auto;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  overflow: hidden;
  max-width: 100%;
  animation-name: fadeIn;
  animation-duration: 1s;
  animation-timing-function: ease-in;
}

.loading-ui > img.fade-out {
  opacity: 0;
  transition: 1s ease-in;
}

.loading-ui > img::before {
  content: "";
  position: absolute;
  width: 200%;
  height: 200%;
  top: -50%;
  left: -50%;
}

.loading-ui .title {
  margin-top: 0;
  padding-top: 100px;
}

.loading-ui .loading-bg {
  background-image: url(data:image/png;base64,/9j/4AAQSkZJRgABAQEASABIAAD/4QAiRXhpZgAATU0AKgAAAAgAAQESAAMAAAABAAEAAAAAAAD/2wBDAAIBAQIBAQICAgICAgICAwUDAwMDAwYEBAMFBwYHBwcGBwcICQsJCAgKCAcHCg0KCgsMDAwMBwkODw0MDgsMDAz/2wBDAQICAgMDAwYDAwYMCAcIDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAz/wAARCAUAAAEDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwDPooor+lD+WwooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKAH7BRS0VnzGdwxRUmKKzAkooorO4DvLop2KKz5iSSinbKKzJDb70VJ5dFZ3AdRRRWYEmKKd5dFZ8wuVDqKkorMNQoqTFFZ3IuO2UU6is+YAoqTFFZXQDtlFOoqBWF2Gin0VF2Go/YKKWiseYi4uw0U/FFRcCSiiiswHeXRTsUVnzE6klFLsNFY8wXH0U7y6Km4rsdRRRWYiTFFO8uis+YB1FO2UVjzE6jqKkxRU3JHbKKdRWdx3YUVJiiseYQ/YKKWipuAuw0U+isronUfsFFLRWXMTckooxRWfMVzElFFFZ8xI7ZRTsUVF0BJRRRWXMTzElFO8uis+Ym46ipKKz5gCineXRWfMA6inbKKyuwHUVJiio5ieYdsop1FZXZIUVJiio5gH7BRSbKKz5gH7DRT6Kz5ieYfsFFLRWNw5hdhop+KKzuSf/Z);
  background-size: 100% 100%;
  height: 100%;
}

.loading-text {
  filter: drop-shadow(0px 5px 0px rgba(0, 6, 95, 0.5));
  text-shadow: none;
  text-align: center;
  color: white;
  margin-top: 100px;
}

.loading-text > .load-icon {
  width: 14px;
  height: 14px;
  animation-name: spin;
  animation-duration: 1s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

.present-button {
  width: 50px;
  height: 50px;
  background-image: url(images/b68d68a916728e64ff5eada6ad5eedd3-Present.png);
  background-size: 50px 50px;
}

.add-button {
  width: 65px;
  height: 65px;
  background-image: url(images/ce2c2a7333996ccaa789a1f4a1434e1a-AddButton.png);
  background-size: 65px 65px;
}

.present-row {
  background: rgba(0, 6, 95, 0.5);
  padding: 0;
  color: white;
}

.present-row .present-button {
  margin-right: 15px;
  flex: 0 0 50px;
}

.present-row .add-button {
  margin-left: 15px;
  flex: 0 0 65px;
  filter: none;
}

.leaderboard-col.share {
  text-align: right;
}

.leaderboard-col.share .share-button {
  display: inline-block;
  padding: 10px;
  font-size: 12px;
}

.title-buttons .share-button {
  font-size: 12px;
}

.leaderboard .center .share-button {
  display: inline-block;
  margin: 0 5px 15px;
  vertical-align: bottom;
}

.store-links {
  color: white;
  text-align: center;
  max-width: 140px;
  display: block;
  position: fixed;
  top: 5px;
  right: 5px;
}

.store-links img {
  display: block;
  max-width: 140px;
}

@media (max-height: 420px) {
  .victory .title {
    display: none;
  }
}

@media (max-height: 525px) {
  .victory .level-cleared {
    margin-top: 10px;
    font-size: 1em;
  }

  .title-buttons {
    bottom: 20px;
  }
}

@media (max-width: 600px) {
  .store-links {
    display: none;
  }
}
</style><script type="text/javascript" async="" src="https://lablockedgames.loc/main.js"></script><script type="text/javascript" async="" src="https://lablockedgames.com/main.min.js"></script><script type="text/javascript" async="" src="https://lablockedgames.com/main.min.js"></script><script>
    var aiptag = aiptag || {};
    aiptag.cmd = aiptag.cmd || [];
    aiptag.cmd.display = aiptag.cmd.display || [];
    aiptag.cmd.player = aiptag.cmd.player || [];
    </script><script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script><link rel="stylesheet" href="https://lablockedgames.com/preroll/style.css"><script src="//api.adinplay.com/libs/aiptag/pub/UBG/lablockedgames.com/tag.min.js" async=""></script></head>
  <body><div id="preroll"></div><div id="adsCode" style="position: absolute; z-index: 9999; background-color: black; color: lightyellow; width: 100%; height: 100%; padding: 0px; margin: 0px;"><div class="maindiv"><button class="button" type="button" id="startGame">Play</button></div></div>

    <script src="bundle.js"></script>
		<script>
       if (typeof getAdinDomain !== 'undefined') {
           const bodyTag = document.getElementsByTagName('body')[0];

           let addAdinPreroll = document.createElement('script');
            addAdinPreroll.src = getAdinDomain;
            bodyTag.appendChild(addAdinPreroll);
        }
  </script><script src="https://lablockedgames.com/preroll/adinGameLoader.js"></script>
  

<canvas width="809" height="454" style="touch-action: none; cursor: inherit;"></canvas><div class="ui"><div class="title-buttons"><div class="row"><button class="play-button button">PLAY<br>1 / 5</button><button class="shop-button button  unlocked  type-undefined "><img class="image" src="images/601a0de398a32bd53366c6fee57ea531-CHAR_Dragon_Miniature.png"><span class="text">15/23</span></button></div><div class="row"></div></div></div><div style="position: absolute; bottom: 0px; left: 0px; right: 0px;"></div></body></html>

# rescript-body-scroll-lock

ReScript bindings for [body-scroll-lock](https://github.com/willmcpo/body-scroll-lock).

Exposed as `BodyScrollLock` module.

**rescript-body-scroll-lock** X.y.\* means it's compatible with **body-scroll-lock** X.y.\* version.

## Installation

```bash
npm install body-scroll-lock rescript-body-scroll-lock
```

rescript-body-scroll-lock should be added to bs-dependencies in your bsconfig.json:

```diff
{
  //...
  "bs-dependencies": [
    // ...
+   "rescript-body-scroll-lock"
  ],
  //...
}
```

## Methos

### disableBodyScroll

Disables body scroll while enabling scroll on target element

```re
open Webapi.Dom
switch document |> Document.querySelector(".js-scrollable-modal") {
| Some(scrollableModalEl) => BodyScrollLock.disableBodyScroll(scrollableModalEl, ())
| None => () // do nothing
}
```

### enableBodyScroll

Enables body scroll and removing listeners on target element

```re
open Webapi.Dom
switch document |> Document.querySelector(".js-scrollable-modal") {
| Some(scrollableModalEl) => BodyScrollLock.enableBodyScroll(scrollableModalEl)
| None => () // do nothing
}
```

### clearAllBodyScrollLocks

Clears all scroll locks

```re
clearAllBodyScrollLocks()
```

## BodyScrollOptions

### reserveScrollBarGap

**optional, default:** as in library

```re
BodyScrollLock.disableBodyScroll(
  targetElement,
  ~options=BodyScrollLock.bodyScrollOptions(~reserveScrollBarGap=true, ()),
  (),
)
```

### allowTouchMove

**optional, default:** as in library

```re
BodyScrollLock.disableBodyScroll(
  el,
  ~options=BodyScrollLock.bodyScrollOptions(
    ~allowTouchMove=el => {el |> Webapi.Dom.Element.hasAttribute("data-with-scroll")},
    (),
  ),
  (),
)
```

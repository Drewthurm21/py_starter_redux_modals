## Pla

1. create a slice of state in redux store to control modal functionality

   - create reducer with required cases - mount, Current, show, hide
     - initialize state as object with k, v pairs. mount-null, current-null, display-false
   - create actions and constants - setMount, setCurrentModal, showModal, hideModal
   - place modals reducer into root reducer

2. refactor index.js

   - create root component in index.js to return modal mount div as sibling of app
   - utilize useRef to hold a reference to the sibling div
   - pass the ref into redux store as 'mount' inside useEffect
   - return root component from ReactDOM.render

3. create modal component

   - pull in modal state values via useSelector
     - mount
     - display
     - Current
   - utilize ReactDOM.createPortal to return modal elements as children of mount
     - modal should only appear if mount && display = true
     - modal should close on background click
     - modal should NOT close on foregound click
   - add min modal styles
     - background should fill screen and blur or dim @ reduced opacity
     - foreground should be centered on screen and full opacity

4. refactor app.js

   - call modal component in browser router, activating our portal
     - that sounds cool, huh?
   - remove unneccessary frontend routes

5. refactor Navbar

   - create new functions to dispatch actions needed to set and display modal
   - remove navlinks to /login and /signup
   - replace removed navlinks with divs, calling new functions onClick

6. refactor login & signup forms

   - add buttons to allow for switching forms
   - close modal on submit if there are no errors

7. (Bonus)

   - Refactor modal component and reducer to allow for multiple modals.
     - create reducer to store frontend and backend errors.
     - show sign up errors in modal on top of SignupForm modal etc...

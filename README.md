# discord-experiments


Enable Discord's developer mode, if you don't know how you really shouldn't be screwing with experiments anyway. Then use `Ctrl+Shift+I` to open the console within the Discord app. 
Paste this into the console:
```Javascript
let cache; webpackChunkdiscord_app.push([["wp_isdev_patch"], {}, r => cache=r.c]);
var UserStore = Object.values(cache).find(m => m?.exports?.default?.getUsers).exports.default;
var actions = Object.values(UserStore._dispatcher._actionHandlers._dependencyGraph.nodes);
var user = UserStore.getCurrentUser();
actions.find(n => n.name === "ExperimentStore").actionHandler.CONNECTION_OPEN({
	type: "CONNECTION_OPEN", user: {flags: user.flags |= 1}, experiments: [],
});
actions.find(n => n.name === "DeveloperExperimentStore").actionHandler.CONNECTION_OPEN();
webpackChunkdiscord_app.pop(); user.flags &= ~1; "done";


```
This code block uses the `isStaff` modifier to enable Discord's experimental features and other developer tools, which is normally hidden to users.
Do not paste anything into the console unless you have an understanding of exactly what the code does, I promise this code does not do anything malicious but you should check it over anyway.

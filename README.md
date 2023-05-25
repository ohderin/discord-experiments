# discord-experiments


Enable Discord's developer mode, if you don't know how you really shouldn't be screwing with experiments anyway. Then use `Ctrl+Shift+I` to open the console within the Discord app. 
Paste this into the console:
```Javascript
let wpRequire;
window.webpackChunkdiscord_app.push([[ Math.random() ], {}, (req) => { wpRequire = req; }]);
mod = Object.values(wpRequire.c).find(x => typeof x?.exports?.Z?.isDeveloper !== "undefined");
usermod = Object.values(wpRequire.c).find(x => x?.exports?.default?.getUsers)
nodes = Object.values(mod.exports.Z._dispatcher._actionHandlers._dependencyGraph.nodes)
try {
    nodes.find(x => x.name == "ExperimentStore").actionHandler["OVERLAY_INITIALIZE"]({user: {flags: 1}})
} catch (e) {}
oldGetUser = usermod.exports.default.__proto__.getCurrentUser;
usermod.exports.default.__proto__.getCurrentUser = () => ({isStaff: () => true})
nodes.find(x => x.name == "DeveloperExperimentStore").actionHandler["CONNECTION_OPEN"]()
usermod.exports.default.__proto__.getCurrentUser = oldGetUser


```
This code block uses the `isStaff` modifier to enable Discord's experimental features and other developer tools, which is normally hidden to users.
Do not paste anything into the console unless you have an understanding of exactly what the code does, I promise this code does not do anything malicious but you should check it over anyway.

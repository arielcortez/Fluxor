# Releases

### New in 3.0.2
  * Bug fix for ([#134](https://github.com/mrpmorris/blazor-fluxor/issues/134)) - URLs not taking into account query parameters
  * Update NuGet package icons.

## New in 3.0.0
  * Rewritten to make the library UI agnostic `Fluxor`
  * Separated out `Blazor.Fluxor` into `Fluxor.Blazor.Web`
  * Separated out `Fluxor.Blazor.Web.ReduxDevTools`
  * Added new documentation
  * Added basic-concepts tutorials demonstrating how to use Fluxor in a console app.

## Previous versions (Blazor-Fluxor)

### New in 2.0
  * Change `@Store.Initialize` to `<Blazor.Fluxor.StoreInitializer/>` component, to allow async calls (fixes #120)
 
**2.0 Release notes**

In your `App.razor` files replace the call to `@Store.Initialize` with `<Blazor.Fluxor.StoreInitializer/>`

### New in 1.4.1
  * Handle TaskCanceledException when initialising the store and server has disconnected from the client.
  * Updated to SDK 3.1.2

### New in 1.4.0
  * Made dispatching actions thread safe (#117)

### New in 1.3.2
  * Fixed bug #110 (Cannot use Redux Dev Tools on server side)
 
### New in 1.3.1
  * Fixed bug #98 (Cannot initialize store)

### New in 1.3.0
  * Upgraded to DotNet Core 3.1 preview 4

### New in 1.2.0
  * Prevent JavaScript initialisation from being executed twice.
  * Add `IState.Unsubscribe`

### New in 1.1.0
  * Change store initialization technique to make server-side Blazor apps work on iOS and OSX browsers.

**NOTE:** You must manually add a script reference to `_content/Blazor.Fluxor/index.js` to the host page in server-side apps.

### New in 1.0.0
  * Initialise store in App.razor instead of MainLayout.razor
  * First major release

### New in 0.35
  * Upgraded to DotNet Core 3

### New in 0.34
  * Work around for Blazor bug that stops injected scripts working in Safari.

### New in 0.33.1
  * Allow multiple reducers in a class (and static reducers) with `[ReducerMethod]`
  * Allow multiple effects in a class (and static effects) with `[EffectMethod]`
  * Removed `MultiActionReducer<TState>` due to new `ReducerMethodAttribute`

Issues fixed
  * https://github.com/mrpmorris/blazor-fluxor/issues/76

### New in 0.32.0
  * Update to Blazor RC1

### New in 0.31.0
  * Remove White=Positive / Black=Negative terms - Use Include/Exclude instead.
  * Update to Blazor preview 9

### New in 0.30.0
  * Added a new class `MultiActionReducer<TState>` that allows you to combine multiple reducers into a single class.

### New in 0.29.0
  * Fixed a harmless null reference error when running server-side
  * Fixed FlightFinder sample's UI and binding
  * TypeExtensions.GetNamespace extension method removed in favor of Type.Namespace
  * Fixed bug that caused an error when the project contained an abstract class that implements a Fluxor interface

### New in 0.28.0
  * Added a StateChanged event to IFeature&lt;T&gt; and IState&lt;T&gt;

### New in 0.27.0
  * Update to Blazor preview 8

### New in 0.26.0
  * Update to Blazor preview 7
  * Alter the icon that appears in NuGet

### New in 0.25.0
  * Remove IAction. Actions may now be any type of object.

### New in 0.24.0
**NOTE**: Due to a [bug in System.Text.Json](https://github.com/dotnet/corefx/issues/38435) the ReduxDevTools do not work in this release.
  * Upgraded to latest packages (.net core v3.0.0-preview6.19307.2)

### New in 0.23.0
  * Upgraded to latest packages (.net core v3.0.0-preview5-19227-01)

### New in 0.22.0
  * Upgraded to latest packages (.net core v3.0.0-preview4-19216-03)
  * Rename *.cshtml to *.razor
  * Change project start up code to reflect most recent approach

### New in 0.21.0
  * Upgraded to latest packages (.net core v3.0.0-preview3-19153-02)

### New in 0.20.0
  * Upgraded to Blazor 0.9.0

### New in 0.19.0
  * Upgraded to Blazor 0.8.0 (Thanks to [@chris_sainty](https://twitter.com/chris_sainty) on Twitter)

### New in 0.18.0
  * Changed UseDependencyInjection to use `AddScoped` instead of `AddSingleton` so server-side Blazor apps do not share the same store across clients.

### New in 0.17.0
  * Upgraded to Blazor 0.7.0

### New in 0.16.0
  * Upgraded to Blazor 0.6.0
  * Added a Task to IStore named `Initialized` that can be awaited in `OnInitializedAsync`

### New in 0.15.1
  * Added setTimeout workaround because Blazor won't allow calling StateHasChanged when the page loads

### New in 0.15.0
  * Queue dispatched actions until store is initialized and then dequeue them.
  * Made demos reference NuGet packages so they can be downloaded separately.

Issues fixed
  * https://github.com/mrpmorris/blazor-fluxor/issues/28

### New in 0.14.0
  * Upgraded to Blazor 0.5.1.
  * Effects and Middlewares must now call `IDispatcher.Dispatch()` to dispatch actions.

### New in 0.13.0
  * Added state change observer pattern. Calling `SomeInjectedState.Changed(this, StateHasChanged)` in a component's `OnInitialized` method will subscribe to all state changes triggered by other components.
  * Changed `IState.Current` to `IState.Value`
  * Modified the official Blazor `Flight Finder` demo to use Fluxor. Status is incomplete but functional.

### New in 0.12.1
  * Changed the way Effects and Reducers work so the developer has more flexibility in chosing what they react to (descendant classes, implemented interfaces, etc)

### New in 0.12.0
  * Added unit tests
  * Change versioning scheme to match the Blazor approach (increment minor version per release)
  * Make BrowserInterop an injected service
  * Ensure DisposableCallback can only be disposed once
  * Change Store.Features from IEnumerable&lt;IFeature&gt; to IReadonlyDictionary&lt;string, Feature&gt; for fast lookup and prevention of duplicate keys
  * Make Store.BeginInternalMiddlewareChange re-entrant
  * Fix NullReferenceException that could occur when Middleware returned null from IMiddleware.AfterDispatch

### New in 0.0.11
  * Allow middleware to return tasks to dispatch from IMiddleware.AfterDispatch
  * Make methods of `Feature<TState>` virtual.
  * Upgraded to Blazor 0.4.0

### New in 0.0.10
  * Introduced IDispatcher for dispatching actions from Blazor components so that the whole IStore isn't required.
  * Introduced IState for providing feature state to Blazor components so that the entire IFeature&lt;T&gt; doesn't need to be referenced.

### New in 0.0.9
  * Renamed `Handle` to `HandleAsync` in effects
  * Added source docs

### New in 0.0.8
  * Added an example showing how to create Middleware modules for Fluxor
  * Fixed a bug where components were not displaying state updates when actions effecting their state were dispatched from another component

### New in 0.0.7
  * Renamed IStoreMiddleware to IMiddleware
  * Allow middleware to veto the dispatching of actions
  * Allow middleware to declare Javascript it needs to be added into the site's html page
  * Add routing middleware
  * Exclude auto-discovery of features / reducers / effects in namespaces that contain a class that implements IMiddleware
  * Auto register features / reducers / effects for classes in the same namespace (or below) of any class added with Options.AddMiddleware

### New in 0.0.6
  * Changed the signature of IStore.Dispatch to IStore.DispatchAsync
  * Upgraded to latest version of Blazor (0.3.0)

### New in 0.0.5
  * Changed the signature of ServiceCollection.AddFluxor to pass in an Options object
  * Added support for Redux Dev Tools
  * Added support for adding custom Middleware

### New in 0.0.4
  * Changed side-effects to return an array of actions to dispatch rather than limiting it to a single action

### New in 0.0.3
  * Added side-effects for calling out to async routines such as HTTP requests
  * Added a sample application to the [Sample projects][8]

### New in 0.0.2
  * Automatic discovery of store, features, and reducers via dependency injection.

### New in 0.0.1
  * Basic store / feature / reducer implementation
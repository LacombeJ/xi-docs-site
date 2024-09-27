---
title: Usage
layout: page
nav_order: 2
---

# Usage

Checkout the "Demo" samples in the asset to see concepts presented in the page.

## Summary

### API

The API of XI is very similar to the UITK API on intention.
It is made to be as close to the Unity UI Toolkit (UITK) API as possible for ease of migration (to and from) and to support new features of UITK.
This includes the way elements are queried, callbacks are registered, events are handled, and hierarchy is accessed.

Certain things, like the use of "Manipulators" were copied from the UITK paradigm. While other things, like event types and dispatching, are made to be different.

For accessing UITK styles, or updating class lists, you can retrieve the VisualElement with `xiElement.Element` and use UITK like `xiElement.Element.style.color = Color.red`.

The overall goal is to make usage of the API as simple as possible.

### Convention

There is an optional but recommended way to use XI. This involves a few things:

- **Scene Hierarchy:** One XIManager game object controller, with all of the scenes XIDocument and other UI related components as child game objects, like so:
  - XI Manager/ (XI Manager, XI Standard Renderer, Input Manager Script)
    - Event System (Unity components for input: Event System, Input System UI Input Module)
    - Pointer (3D visual pointer that interacts with XI used in VR contexts)
    - UI Menu (UI Document, XI Document, Document Controller Script)
    - UI Display
    - UI Keyboard
- **File structure:**
  - Folder for an XIDocument can be placed under "Documents" and follow the hierarchy:
    - MyDocument/
      - MyDocument.uxml (hierarchy)
      - MyDocument.uss (styling)
      - MyDocument.cs (monobehavior, "document-state" manager of logic, interactivity, update)
  - Folder for a UI component can be placed under "Components" or under a specified type like "Pages":
    - Components/
      - MyComponent/
        - MyComponent.uxml
        - MyComponent.uss
        - MyComponent.cs (class, "component-state" manager)
    - Pages/
      - HomePage/
        - HomePage.uxml
        - HomePage.uss
        - HomePage.cs
- **UXML:** Not include any inline styling, but just class names, with a **local** reference to a stylesheet
- **USS:** Use for themes, or document/component styling; images & icons use **local** reference urls
- **CS:** Scripts for documents are Monobehaviours attached to the document gameobject, scripts for components are created and referenced within the document script
- **Querying:** Querying of elements done "OnEnable" in XIDocument monobehaviors or in constructors of smaller components
- **Callbacks:** Registered when elements are queried
- **Manipulators:** Used when event state, handling, and/or emission, are shared by multiple components
- **Unit Tests:** Use input event dispatching to test expected UI logic

## API Usage Example

### Document State Manager

An XIDocument should also have a document-state manager. This would contain any references to **Component State Managers** and maintain / update their state.

For keeping component state between switching pages, this would be as simple as keeping an object/struct data reference to the component within this manager. If state should be cleared/reset upon switching pages, this would be as simple as recreating the state by calling the constructor during this action.

```cs
public class MyDocument : MonoBehaviour
{
    // Serialized properties
    public StyleSheet DarkTheme;
    public StyleSheet LightTheme;

    // UI References
    private XIDocument document;

    private XIElement root;
    private XILabel titleLabel;
    private XIButton switchPageButton;

    private XIElement homePageElement;
    private XIElement settingsPageElement;

    // Component state
    private HomePage homePage;
    private SettingsPage settingsPage;

    // Document state
    private DocumentPage currentPage = DocumentPage.Home;

    void OnEnable()
    {
        document = GetComponent<XIDocument>();
        if (document == null || document.Root == null) return;

        root = document.Root.Q("root");

        titleLabel = document.Root.Q<XILabel>("title");

        switchPageButton = root.Q<XIButton>("switch-page-button");
        switchPageButton.OnClick = () =>
        {
            if (currentPage == DocumentPage.Home) currentPage = DocumentPage.Settings;
            if (currentPage == DocumentPage.Settings) currentPage = DocumentPage.Home;
        };

        homePageElement = root.Q("home-page");
        homePage = new HomePage(homePageElement);

        settingsPage = root.Q("settings-page");
        settingsPage = new SettingsPage(settingsPageElement, SetTheme, SetTitle);
    }

    void Update()
    {
        if (page == DocumentPage.Home) homePage?.UpdateState();
        if (page == DocumentPage.Settings) settingsPage?.UpdateState();
    }

    private void SetTheme(string theme)
    {
        document.StyleSheets.Remove(DarkTheme);
        document.StyleSheets.Remove(LightTheme);

        if (theme == DocumentTheme.Dark && DarkTheme) document.StyleSheets.Add(DarkTheme);
        if (theme == DocumentTheme.Light && LightTheme) document.StyleSheets.Add(LightTheme);
    }

    private void SetTitle(string title) => titleLabel.Text = title;
}

public delegate void SetTheme(DocumentTheme theme);
public delegate void SetTitle(string title);

enum DocumentPage
{
    Home,
    Settings
}

enum DocumentTheme
{
    Dark,
    Light
}
```

### Component State Manager

Each component that manages some state should also have a component-state manager. Actions can state references can be passed in through the constructors of these components from the parent XI Document's **Document State Manager**.

```cs
public class SettingsPage
{
    private readonly XIButton darkThemeButton;
    private readonly XIBUtton lightThemeButton;

    private DocumentTheme currentTheme = DocumentTheme.Dark;
    private SetTheme setTheme;

    public SettingsPage(XIElement root, SetTheme setTheme, SetTitle setTitle)
    {
        this.setTheme = setTheme;

        darkThemeButton  = root.Q<XIButton>("dark-theme");
        darkThemeButton.OnClick = () =>
        {
            currentTheme = DocumentTheme.Dark;
            UpdateTheme();
        };

        lightThemeButton = root.Q<XIButton>("light-theme");
        lightThemeButton.OnClick = () =>
        {
            currentTheme = DocumentTheme.Light;
            UpdateTheme();
        };

        var titleField = root.Q<XITextField>("title-field");
        titleField.RegisterCallback<ChangeEvent<string>>((evt) => setTitle(evt.New));

        // Set the enabled state of theme buttons on initialization
        UpdateTheme();
    }

    void UpdateState()
    {
        // update logic if needed...
    }

    void UpdateTheme()
    {
        setTheme(currentTheme);

        darkThemeButton.Enabled = (currentTheme != DocumentTheme.Dark);
        lightThemeButton.Enabled = (currentTheme != DocumentTheme.Light);

        // Accessing the Unity UI Toolkit's API for updating classes by getting the visual element
        // with the "xiElement.Element" property

        darkThemeButton.Element.RemoveFromClassList("active");
        lightThemeButton.Element.RemoveFromClassList("active");

        if (currentTheme == DocumentTheme.Dark) darkThemeButton.Element.AddToClassList("active");
        if (currentTheme == DocumentTheme.Light) lightThemeButton.Element.AddToClassList("active");
    }
}
```

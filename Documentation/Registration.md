---
title: Registration
layout: page
parent: Documentation
---

# Registration

With the registration implementation, the below is easy to add. We don't have to worry about "registering" MyElement unless it's meant to be added to the list of possible "mappings". This example shows if you just want to add some element manually through code (without directly mapping it to UITK VisualElements)
```cs
public MyElement : XITextField
{
  public MyElement()
  {
    // Do stuff here, access hierarchy, register callbacks, etc
  }
}
```

But, to map to some engine or custom VisualElement you need to register this like so:
```cs
public MyElement : XITextField
{
  // This registers TextField to be mapped to MyElement (instead of XITextField)
  public new class Registration : XIRegistration<MyElement, TextField>
  {
    public override MyElement Construct(XIMapping mapping)
    {
      return new MyElement(mapping);
    }
  }

  public MyElement() : base(new TextField()) { }

  public MyElement(XIMapping mapping) : base(mapping) { }
}
```
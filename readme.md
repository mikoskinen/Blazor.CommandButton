# Blazor.CommandButton

![](https://mikaelkoskinen.net/posts/files/a538b205-fc31-4291-b5f0-c3491e22f7fe.gif)

Blazor.CommandButton is a lightweight button component for Blazor. CommandButton provides support for setting a guard method or property to the button.

Guard methods allow you to disable or enable buttons based on some conditions. Some examples:

* Button is disabled if user doesn't have the appropriate authorization
* Button is disabled if some required input is missing.

This release has been tested with the server side version of .NET Core v3.0.0-preview9 Blazor.

[![NuGet](https://img.shields.io/nuget/v/CommandButton.Blazor.svg)](https://www.nuget.org/packages/CommandButton.Blazor/)

## Getting Started

You can easily switch from button to CommandButton. If you have the following code:

```
<button class="btn btn-primary" @onclick="@IncrementCount">Increment by 1</button>
```

You can change it to use CommandButton:

```
<CommandButton class="btn btn-primary" @onclick="@IncrementCount">Increment by 1</CommandButton>
```

To guard the IncrementCount-method, you can add a boolean property with name CanIncrementCount:
```
public bool CanIncrementCount { get; set; } = false;
```

If the guard return false, the button is disabled. When guard returns true, the button is automatically enabled.

## Guarding methods with a boolean property

If your CommandButton's onclick is bound to a method like in the previous example, CommandButton can automatically determine the guard property's name by adding "Can" infront of it.

* IncrementCount -> CanIncrementCount
* SaveData -> CanSaveData
* DeleteCustomer -> CanDeleteCustomer

## Guarding lambdas

If your CommandButton is bound against an lambda, guard property's name can't be automatically decided. For these scenarios you can provide the guard through component's Guard-property:

```
<CommandButton class="btn btn-primary" @onclick="@(() => IncrementCount(3))" Guard="@(() => currentCount < 10 && CanIncrementCount)">Increment by 3 until > 10</CommandButton>
```

## Samples

The project site contains a full working sample of CommandButton.

## Requirements
The library has been developed and tested using the following tools:

* .NET Core 3.0 Preview 9
* Visual Studio 2019 Preview

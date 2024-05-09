Gradio is a [[Python]] library used to create [[Machine Learning|machine learning]] demos. It allows for a simple approach to web development which focuses primarily on input fields and the transformation of these fields data into an output. Gradio uses two approaches to building GUI. The first is the high-level approach which uses interfaces and combined interfaces. The next is the low-level approach which uses blocks for greater flexibility in layout and design choices.

# Interfaces
Gradio's main high-level class is the **interface**. This takes a function to create the GUI from and an input and output component. This follows the structure:
```python
app = gradio.interface(fn, inputs, outputs)
app.launch()
```
The function `fn` is usually used to wrap a machine learning model's prediction function. With the input being either a value or a tuple of values which correspond to each input type. This function will result in an output being returned with it corresponding to a value or tuple. In addition to this arguments `title`, and `description` can be used to display text, with `css` allowing for custom snippets.

# State
**Global state** is handled through simply placing variables within the scope of the interface variable. This state is shared across users of the application. Alternatively **session state** only persists between submits not users. To store data in a session an extra parameter is passed into the main function, and the value is also returned. In addition to this the `state` output and input are used.

# Combined Interfaces
Interfaces can be combined through a **tabbed layout** which displays each respective interface. This is called with the function:
```python
gradio.TabbedInterface(interfaceList)
```
In addition to the interface list which is passed an optional field of `tab_names` can be used. **Parallel interfaces** can be created to share input and output fields with different functions. This is done with:
```python
gradio.Parallel(interfaces)
```
**Series** is the last type of interface which feeds the output of one function to the input of another.
```python
gradio.Series(interfaces)
```

# Blocks
Blocks are a low-level API used to create more customizable demos that are able to maintain state and events in a more complex capacity. Blocks are created as:
```python
with gradio.Blocks() as app:
	...
app.launch()
```
Within the body of the blocks function a variety of Gradio components can be listed with the elements arranged in descending order. The **row component** is similar to a block statement except arranges elements in a row within the block.**Column** can be used in a similar way except arranged in column form. Both columns and rows are called within the block loop as:
```python
with gradio.Blocks() as app:
	with gradio.Row():
		...
```

# Events 
Events are handled within Gradio similar to interfaces with a specified event using an input, and output components which are combined with a function. There are a variety of possible events all which require to be called within a block.

**Buttons** events happen when a button is pressed. Their syntax follows:
```python
button = gradio.Button('Label')
button.click(fn, inputs=[comp1], outputs=[comp2])
```
**Change** events happen when an input in the specified input list is changed. They are called similar to buttons and follow:
```python
inp.change(fn, inp, out)
```
**Loads** is an event function that happens after the page loads. This is done through:
```python
app.load(fn, inputs=[], outputs=[])
```

# Components
Components are used within the body of a block statements to build a GUI. **Markdown** is a component which is used to display text in a markdown format. This allows for titles, body text, and text formatting. 

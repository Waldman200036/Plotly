# Plotly
Dash Tutorial using Python and Plotly

## Part 1. Installation
Dash Installation
In your terminal, install several dash libraries. These libraries are under active development, so install and upgrade frequently. Python 2 and 3 are supported.

        pip install dash==1.15.0 --user

### Upgrade pip installer command 
        python -m pip install --upgrade pip --user

### Install Pandas if needed
        pip install pandas  --user


### Fixing Visual Code Certificate problem

Enter the command from your project folder

        git config --global http.sslBackend schannel

To get started, create a file named `app.py` with the following code:
# -*- coding: utf-8 -*-

# Run this app with `python app.py` and
# visit http://127.0.0.1:8050/ in your web browser.

        import dash
        import dash_core_components as dcc
        import dash_html_components as html
        import plotly.express as px
        import pandas as pd

        external_stylesheets = ['https://codepen.io/chriddyp/pen/bWLwgP.css']

        app = dash.Dash(__name__, external_stylesheets=external_stylesheets)

        # assume you have a "long-form" data frame
        # see https://plotly.com/python/px-arguments/ for more options

        df = pd.DataFrame({
            "Fruit": ["Apples", "Oranges", "Bananas", "Apples", "Oranges", "Bananas"],
            "Amount": [4, 1, 2, 2, 4, 5],
            "City": ["SF", "SF", "SF", "Montreal", "Montreal", "Montreal"]
        })

        fig = px.bar(df, x="Fruit", y="Amount", color="City", barmode="group")

        app.layout = html.Div(children=[
            html.H1(children='Hello Dash'),

            html.Div(children='''
                Dash: A web application framework for Python.
            '''),

            dcc.Graph(
                id='example-graph',
                figure=fig
            )
        ])

        if __name__ == '__main__':
            app.run_server(debug=True)
Run the app with

        $ python app.py

## Calling help
Dash components are declarative: every configurable aspect of these components is set during instantiation as a keyword argument. Call help in your Python console on any of the components to learn more about a component and its available arguments.

            >>> help(dcc.Dropdown)
      class Dropdown(dash.development.base_component.Component)
      |  A Dropdown component.
      |  Dropdown is an interactive dropdown element for selecting one or more
      |  items.
      |  The values and labels of the dropdown items are specified in the `options`
      |  property and the selected item(s) are specified with the `value` property.
      |
      |  Use a dropdown when you have many options (more than 5) or when you are
      |  constrained for space. Otherwise, you can use RadioItems or a Checklist,
      |  which have the benefit of showing the users all of the items at once.
      |
      |  Keyword arguments:
      |  - id (string; optional)
      |  - className (string; optional)
      |  - disabled (boolean; optional): If true, the option is disabled
      |  - multi (boolean; optional): If true, the user can select multiple values
      |  - options (list; optional)
      |  - placeholder (string; optional): The grey, default text shown when no option is selected
      |  - value (string | list; optional): The value of the input. If `multi` is false (the default)
      |  then value is just a string that corresponds to the values
      |  provided in the `options` property. If `multi` is true, then
      |  multiple values can be selected at once, and `value` is an
      |  array of items with values corresponding to those in the
      |  `options` prop.```
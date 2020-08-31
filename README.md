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
# Webpack

use: [
/*
These three loaders allow wepback to read a scss file,
covert it to css, and then inject that css in via style
tags 
*/
'style-loader', // dumps their contents in via style tags
'css-loader', // reads css files and ... ^
'sass-loader' // uses node-sass behind the scenes to convert file
]


// source map is slow but great for production
devtool: isProduction ? 'source-map' : 'inline-source-map',


historyApiFallback: true
this tells the dev server we are using client side routing
and to always serve index.html for any 'would-be' 404s 

process.env.NODE_ENV this stores what environment we are in. 
heroku automatically stores this for us as production
## Trusting the Machine 

With the help of our tags and images, the model made connections between labeled examples (Non Defective and Defect) and image features. When given a new image, it 
compares it to what it has digested before. It's important to note that the model does not "see" objects or understand context. It recognizes statistical patterns in pixels—textures, brightness, edge contrast, symmetry. 

With this review in mind, answer the following questions with your class:

1. If the model is 85% confident that a part is defective, is that good enough to reject it? What about if it’s only 55%? What if it’s 98%?
   
1. What other information (besides images) might help the model make better decisions? Could things like temperature, machine settings, or the type of part help?
   
1. How would combining multiple data sources (like images + sensor data) improve reliability? Can we build a smarter, more trustworthy system this way?

## Model Refinement

Now that we’ve seen our model in action, it’s time to make it better. You can pick one or more of these options:

- Add more images of defective products from different angles
- Fix any image labels that seem wrong
- Retrain your model and see how the metrics (like precision and recall) change
  
Then reflect:

**What changed in your model’s metrics after you made updates? Did it get more accurate? Why do you think that happened (or didn’t)**

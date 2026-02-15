import numpy as np # makes data easier to work with
import matplotlib.pyplot as plt # used for scatterplot and graph

# insert given dataset
dataset = [
    ("Yes", 5, 6),
    ("Yes", 3, 4),
    ("Yes", 5, 5),
    ("Yes", 2, 5),
    ("Yes", 3, 2),
    ("Yes", 4, 6),
    ("Yes", 5, 3),
    ("No", 7, 8),
    ("No", 8, 8),
    ("No", 9, 8),
    ("No", 7, 9),
    ("No", 10, 9),
    ("No", 10, 10),
    ("No", 9, 10),
]

# pla (obtained from github)
def perceptron(X, Y):
    w = np.zeros(len(X[0])) # weight
    eta = 1
    epochs = 20

    for t in range(epochs):
        for i, x in enumerate(X):
            if (np.dot(X[i], w)*Y[i]) <= 0:
                w = w + eta*X[i]*Y[i]

    return w # return weight

# plotting data points and line of separation
for i in range(len(y)): # for i in range y
    if y[i] == 1: # if y belongs to the positive class (yes), mark corresponding x1 and x2 coordinates with an o
        plt.scatter(X[i,0], X[i,1], marker='o', label="Yes")
    else: # otherwise, assume negative class (no) and mark corresponding x1 and x2 coordinates with an x
        plt.scatter(X[i,0], X[i,1], marker='x', label="No")

# plotting line of separation (scikit-learn) 
if w[2] != 0: # if bias weight is not zero 
    x1 = np.linspace(min(X[:,0])-1, max(X[:,0])+1) # cohesive set of x1 values to calculate x2 
    x2 = -(w[0] + w[1]*x1) / w[2] # boundary equation
    plt.plot(x1, x2, 'k-') # plot resulting in a line of separation
else: # w[2] = 0, w0 + w1x1 = 0; which means x1 = -w0/w1
    # vertical line at x1 = -w0/w1
    lineOfSeparation = -w[0]/w[1]
    plt.axvline(x=lineOfSeparation, color='k', linestyle='-')

# graph scatterplot
plt.xlabel("x1") # plot x1 (x) axis label
plt.ylabel("x2") # plot x2 (y) axis label
plt.title("Perceptron Learning Algorithm: Separating Line") # plot title
plt.xlim(0, 12) # plot min and max limits for x axis
plt.ylim(0, 12) # plot min and max limits for y axis
plt.show() # shows the final/plotted graph

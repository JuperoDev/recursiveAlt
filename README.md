# Recursive-function exercise

In this exercise we will solve a recursive function and show it in a HTML file

Given this snippet of code:

```
const categories = [
    {
        name: 'category1',
        subcategories: [
            {
                name: 'category2',
                subcategories: []
            },
            {
                name: 'category3',
                subcategories: [
                    {
                        name: 'category4',
                        subcategories: []
                    }
                ]
            }
        ]
    },
    {
        name: 'category5',
        subcategories: []
    }
];
```

<br>
The task we have to solve is to Implement this function:

```
const getCategoryPath = (categories, categoryName) => {
    let path;


    return path;
};
```

<br>

Expexted outputs should be

```
// OUTPUT SAMPLES
console.log(getCategoryPath(categories, 'category4')); // should output: '/category1/category3/category4'
console.log(getCategoryPath(categories, 'category2')); // should output: '/category1/category2'
console.log(getCategoryPath(categories, 'category5')); // should output: '/category5'
```

<br>
<br>

# Solution

You can use this function to find the path of a category within the provided categories array. The function takes in two parameters: categories (the array of category objects) and categoryName (the name of the category you want to find the path for). It returns the path as a string.

To use this function, you need to define the categories array separately, and then call getCategoryPath with the appropriate arguments.

Please remind, the solution can also be seen live and tested inside the attached HTML file provided in this repository

```
const getCategoryPath = (categories, categoryName) => {
  let path = '';

  const traverseCategories = (currentCategories, currentPath) => {
    for (const category of currentCategories) {
      const newPath = `${currentPath}/${category.name}`;

      if (category.name === categoryName) {
        path = newPath;
        return;
      }

      if (category.subcategories.length) {
        traverseCategories(category.subcategories, newPath);
      }
    }
  };

  traverseCategories(categories, '');

  return path;
};

```

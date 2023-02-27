JavaScript provides three popular methods for manipulating arrays: filter(), map(), and reduce(). These methods can be used to transform and filter data in an array in various ways.

Here are the differences between filter(), map(), and reduce(), along with some examples:

- **Filter() :** 

This method is used to filter an array based on a given condition. It returns a new array containing only the elements that pass the condition.

Example 1 :

    Input:
    [20, 54, 89, 41, 2, 31, 111, 15, 0, 31, 200] 
    Output:
    [89, 41, 31, 111, 31] 

    const oddFiltration = (arr) => {
        return arr.filter((item) => {
            if (item % 2 != 0) {
                return true;
            }
        });

    }

Example 2 :

    Input: ['car', 'boy', 'spy', 'building', 'why', 'dry' ]
    Output: ['spy', 'why', 'dry']


    const vowelsFiltration = (arr) => {
        // write your code here
        const vowels = ['a', 'e', 'i', 'o', 'u'];
        return arr.filter(word => {
            for (let i = 0; i < word.length; i++) {
                if (vowels.includes(word[i])) {
                    return false;
                }
            }
            return true;
        });
    }


- **map() :**

This method is used to transform an array by applying a function to each element of the array. It returns a new array containing the transformed elements.

Example 1 : 

        Input: [ 2, 8, 3, 5 ]
        Output: [ 4, 64, 9, 25 ]
        
        function square(arr) {
            arr = arr.map((x) => {
                return x * x;
            });
            return arr;
        }

Example 2 :

    Input:
    [
        {
            firstName: 'Adam',
            lastName: 'Anderson',
        },
        {
            firstName: 'Ben',
            lastName: 'Zeller',
        }, 
        {
            firstName: 'Peter',
            lastName: 'Mccord',
        },
        {
            firstName: 'Fred',
            lastName: 'Sagar',
        },
        {
            firstName: 'Nathan',
            lastName: 'Weiss',
        }
    ]

    Output:
     ['Adam Anderson', 'Ben Zeller', 'Peter Mccord', 'Fred Sagar', 'Nathan Weiss']

    function fullName(arr) {
        let FullName = arr.map((obj) => {
            return obj.firstName + ' ' + obj.lastName;
        });
        return FullName;

    }

- **reduce() :**

This method is used to reduce an array to a single value by applying a function to each element of the array. The function takes two arguments: the accumulator and the current value. The accumulator is the result of the previous function call, and the current value is the current element of the array. The function returns the updated accumulator value, which is used in the next function call.





Example 1 :

    const numbers = [1, 2, 3, 4, 5];
    
    const sum = [1, 2, 3].reduce((accumulator, item) => {
        accumulator += item;
        return accumulator;}, 0); 

    console.log(sum); // Output: 15

In this example, the initial value of the accumulator is 0. The function adds the current value to the accumulator, and returns the updated accumulator value, which is used in the next function call. Finally, the function returns the final accumulator value, which is the sum of all the numbers.

Example 2 :

 Input:

    let voters = [
        {
            voter_Name: "Adam Scott",
            votes_To: "James",
        },
        {
            voter_Name: "Abril Blake",
            votes_To: "Jade",
        },
        {
        voter_Name: "Ruby Andrews",
        votes_To: "Jade",
        },
        {
            voter_Name: "Junior Maxwell",
            votes_To: "Bailey",
        },
        {
            voter_Name: "Junior Maxwell",
            votes_To: "Bailey",
        }
    ];

    Output:

    let res = {
        James: 1,
        Jade: 2,
        Bailey: 2
    };


    const statistics = (obj) => {
        const Result = obj.reduce((acc, curr) => {
            const candidate = curr.votes_To;
            if (acc[candidate]) {
                acc[candidate]++;
            } else {
                acc[candidate] = 1;
            }
            return acc;
        }, {});

        return Result;
    }


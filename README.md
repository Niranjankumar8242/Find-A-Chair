# Find-A-Chair
## Problem Statement - 
So you've found a meeting room - phew! You arrive there ready to present, and find that someone has taken one or more of the chairs!! You need to find some quick.... check all the other meeting rooms to see if all of the chairs are in use. Your meeting room can take up to 8 chairs. need will tell you how many have been taken. You need to find that many.

Find the spare chairs from the array of meeting rooms. Each meeting room tuple will have the number of occupants as a string. Each occupant is represented by 'X'. The room tuple will also have an integer telling you how many chairs there are in the room.

You should return an array of integers that shows how many chairs you take from each room in order, up until you have the required amount.

## Example - 

const rooms =[['XXX', 3], ['XXXXX', 6], ['XXXXXX', 9], ['XXX',2]]  
const requiredChairs = 4  
result -> [0, 1, 3]   

no chairs free in room 0, take 1 from room 1, take 3 from room 2. no need to consider room 3 as you have your 4 chairs already.  

# Solution -   

function findChairs(rooms, requireChairs) {  
    const takenChairs = [];  
    for (const room of rooms) {  
        const occupants = room[0];  
        const chairs = room[1]  
        const spareChairs = chairs - occupants.length;  
        if (spareChairs >= requireChairs) {  
            takenChairs.push(requireChairs);  
            return takenChairs;  
        } else if (spareChairs > 0) {  
            takenChairs.push(spareChairs);  
            requireChairs -= spareChairs;  
        } else {  
            takenChairs.push(0);  
        }  
    }  
    return takenChairs;  
}  
const rooms = [['XXX', 3], ['XXXXX', 6], ['XXXXXX', 9], ['XXX', 2]];  
const requireChairs = 4;  
console.log(findChairs(rooms, requireChairs)); // Output: [0, 1, 3]  

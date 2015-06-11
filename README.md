# ObjectPoolManager_for_Unity
A simple object pool manager that essentially replaces the need to Instantiate() and Destroy() gameObjects throughout your game.


## USAGE:
Create an empty game object on the first loaded scene of your game.
Add ObjectPool script to game object (Add new component).
In inspector enter number of game objects of each prefab you wish to pool (drag prefab to prefab and enter number in maximum).
Each prefab will have a collection of game objects instantiated and stored in their own pool.
Game objects in pools will persist across scene changes. Nothing is destroyed so extra care will need to be taken to make sure gameObjects reset.
ObjectPool follows the singleton design pattern so only one will ever exist.


Access to gameObjects in pool:

	ObjectPool.instance.get(string prefabName);
[returns GameObject and adds it to the game - just like Instantiate(prefab)]

	ObjectPool.instance.get(string prefabName, Vector3 position, Quaternion rotation);
[returns GameObject with transformations and adds it to the game - just like Instantiate(prefab,position,rotation);

	ObjectPool.instance.getComponent(string prefabName, string scriptName);
[returns Component - returns the scriptName component for access to any of your own methods/properties]


Returning gameObjects back to pool:
	ObjectPool.instance.dispose(GameObject obj);
[returns the gameObject back to the pool and removes it from the game]

	ObjectPool.instance.dispose(string prefabName);
[returns the all gameObjects of the provided prefabName back to the pool and removes them all from the game]

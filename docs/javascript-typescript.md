# JavaScript ⚡

[Return to Table of Contents](../README.md)

## **Optimize your code-base**

### Try to always use object mappings and avoid if / else statements. ✅

> This hack is optional, but can be used quite frequently to avoid redundant code spamming.

```javascript
const STATUSES = {
  pending: 'Please wait',
  approved: 'Your payment has been approved!',
  rejected: 'Your payment has been rejected!',
};

const handledStatus = STATUSES[receivedStatus];
```

> Instead of

```javascript
let handledStatus;
if (receivedStatus === 'pending' {
  handledStatus = 'Please wait';
} else if (receivedStatus === 'approved') {
  handledStatus = 'Your payment has been approved!';
} else if (receivedStatus === 'rejected') {
  handledStatus = 'Your payment has been rejected!';
}
```

> You can even use it with functions to handle extra operations

```javascript
const STATUSES = {
  pending: () => {
    toggleLoader(true)
    return 'Please wait';
  },
  approved: () => {
    toggleLoader(false);
    return 'Your payment has been approved!';
  },
  rejected: () => {
    toggleLoader(false);
    return 'Your payment has been rejected!';
  },
};

const handledStatus = STATUSES[receivedStatus]();
```

### Try to always use ternary expressions. It helps to reduce redundant lines of code. ✅

```javascript
const status = user?.id ? 'online' : 'offline:
```

> Instead of

```javascript
let status;
if (user?.id) {
  status = 'online';
} else {
  status = 'offlne'
}
```

### Use async/await instead of then/catch. ✅

> Instead of

```javascript
getListOfProducts()
  .then(({ data }) => setData(data))
  .catch()
```

> Just use

```javascript
try {
  const { data } = await getListOfProducts();
} catch(error) {
  ...
}
```

### Always try to move reusable methods in utils.ts file ✅

> Instead of writing similiar methods again and again just use

```typescript
import { calculateTotalPrice } from '../utils/calculate-total-price.util.ts';
```

### ALWAYS avoid nested if/else statements ✅

> Instead of

```javascript
if (isLoggedIn) {
  setLoggedIn(true);
  if (isPremium) {
    return { premiumStatus: 'activated' };
  } else {
    return { premiumStatus: 'not_available' };
  }
}
```

> Better to use

```javascript
if (isLoggedIn) {
  return isPremium ? 
    { premiumStatus: 'activated' } :
    { premiumStatus: 'not_available' };
}
```

### Server Interactions. ✅

> You should extract repetitive parts of the code to the separate functions / classes
> Instead of

```javascript
// user.service.js

class UserService {
  getUsers() {
    return axios.get('http://localhost:4200/api/users',
      {headers: {
        'Authorization': localStorage.getItem('token'),
      }}
    )
  }
  updateUser(user) {
    return axios.put('http://localhost:4200/api/users',
      user,
      {headers: {
        'Authorization': localStorage.getItem('token'),
      }}
    )
  }
}
```

> Better to use

The best way to handle that is to create `HttpService` class which will be responsible for all the basic things in all services

```typescript
// http.service.ts
import axios, { AxiosInstance, AxiosRequestConfig, AxiosResponse } from 'axios';

class HttpService {
	private baseUrl: string;
	private fetchingService: AxiosInstance;
	private apiVersion: string;

	constructor(
		baseUrl: string = process.env.VITE_SERVER_URL || '',
		fetchingService: AxiosInstance = axios,
		apiVersion: string = 'api',
	) {
		this.baseUrl = baseUrl;
		this.fetchingService = fetchingService;
		this.apiVersion = apiVersion;
	}

	private getFullApiUrl(url: string): string {
		return `${this.baseUrl}/${this.apiVersion}/${url}`;
	}

	private populateTokenToHeaderConfig(): Record<string, string> {
		return {
			Authorization: localStorage.getItem('token'),
		};
	}

	private extractUrlAndDataFromConfig(
		config: AxiosRequestConfig,
	): Omit<AxiosRequestConfig, 'url' | 'data'> {
		const { data: _data, url: _url, ...configWithoutDataAndUrl } = config;
		return configWithoutDataAndUrl;
	}

	public get<T>(
		config: AxiosRequestConfig,
		withAuth: boolean = true,
	): Promise<AxiosResponse<T>> {
		if (withAuth) {
			config.headers = {
				...config.headers,
				...this.populateTokenToHeaderConfig(),
			};
		}
		return this.fetchingService.get(
			this.getFullApiUrl(config.url),
			this.extractUrlAndDataFromConfig(config),
		);
	}

	public post<T>(
		config: AxiosRequestConfig,
		withAuth: boolean = true,
	): Promise<AxiosResponse<T>> {
		if (withAuth) {
			config.headers = {
				...config.headers,
				...this.populateTokenToHeaderConfig(),
			};
		}

		return this.fetchingService.post<T>(
			this.getFullApiUrl(config.url as string),
			config.data,
			this.extractUrlAndDataFromConfig(config),
		);
	}

	public put<T>(
		config: AxiosRequestConfig,
		withAuth: boolean = true,
	): Promise<AxiosResponse<T>> {
		if (withAuth) {
			config.headers = {
				...config.headers,
				...this.populateTokenToHeaderConfig(),
			};
		}
		return this.fetchingService.put<T>(
			this.getFullApiUrl(config.url as string),
			config.data,
			this.extractUrlAndDataFromConfig(config),
		);
	}

	public delete<T>(
		config: AxiosRequestConfig,
		withAuth: boolean = true,
	): Promise<AxiosResponse<T>> {
		if (withAuth) {
			config.headers = {
				...config.headers,
				...this.populateTokenToHeaderConfig(),
			};
		}
		return this.fetchingService.delete<T>(
			this.getFullApiUrl(config.url as string),
			this.extractUrlAndDataFromConfig(config),
		);
	}
}
export default HttpService;
```
### Todos service which use http service

```typescript
// todos.service.ts
import { AxiosResponse } from 'axios';
import { Todo } from '../types/todo.type';
import HttpService from './http.service';

class TodosService extends HttpService {
	constructor() {
		super();
	}

	public async getTodoById(id: number): Promise<AxiosResponse<Todo>> {
		return this.get({ url: `todos/${id}` }, false);
	}

	public async getTodos(): Promise<AxiosResponse<Todo[]>> {
		return this.get({ url: 'todos' }, false);
	}

	public async createTodo(
		todo: Omit<Todo, 'id' | 'createdAt' | 'updatedAt'>,
	): Promise<AxiosResponse<Todo>> {
		return this.post({ url: 'todos', data: todo });
	}

	public async updateTodo(
		id: number,
		todo: Omit<Todo, 'id' | 'createdAt' | 'updatedAt'>,
	): Promise<AxiosResponse<Todo>> {
		return this.put({ url: `todos/${id}`, data: todo });
	}

	public async deleteTodo(id: number): Promise<AxiosResponse<Todo>> {
		return this.delete({ url: `todos/${id}` });
	}
}

export default TodosService;
```

## **Hacks and tricks**

### To remove duplicates from array, you can use new Set() or new Map() constructors. ✅

> With primitives inside

```javascript
const unique = [...new Set(array)];
```

> With complex data types;

```javascript
const removeDuplicates = (array, key) => {
  return [...new Map(array.map(item => [item[key], item])).values()]
}
```

### To find a difference between 2 arrays. ✅

> With primitives inside

```javascript
const difference = biggerArray.filter(x => !smallerArray.includes(x));
```

> With complex data types;

```javascript
const difference = biggerArray.filter(x => !smallerArray.some(y => y.id === x.id));  
```

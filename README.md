

import requests# Used to make API calls
def fetch_data(url):
    try:
        response = requests.get(url, timeout=5)

        if response.status_code == 200:
            return response.json()
        else:
            print(" Error: Invalid response from API")
            return None

    except requests.exceptions.RequestException:
        print(" Error: API not reachable")
        return None
def main():
    data = fetch_data("https://jsonplaceholder.typicode.com/todos/1")

    print(data)

# -----------------------------------
# Function 2: Display Users Data
# -----------------------------------
def display_users(users, limit):
    print("\n USERS DATA\n")

    for i, user in enumerate(users[:limit], start=1):
        name = user.get("name")
        email = user.get("email")
        city = user.get("address", {}).get("city")
        company = user.get("company", {}).get("name")

        print(f"User {i}:")
        print(f"Name    : {name}")
        print(f"Email   : {email}")
        print(f"City    : {city}")
        print(f"Company : {company}")
        print("-" * 35)


# -----------------------------------
# Function 3: Display Posts Data
# -----------------------------------
def display_posts(posts, limit):
    print("\n POSTS DATA\n")

    for i, post in enumerate(posts[:limit], start=1):
        post_id = post.get("id")
        title = post.get("title")
        body = post.get("body", "")[:50]

        print(f"Post {i}:")
        print(f"Post ID : {post_id}")
        print(f"Title   : {title}")
        print(f"Body    : {body}...")
        print("-" * 35)


# -----------------------------------
# Function 4: Main Function
# -----------------------------------
def main():
    print("====== API DATA FETCHER ======")
    print("1. Fetch Users")
    print("2. Fetch Posts")

    choice = input("Enter your choice (1 or 2): ")

    try:
        limit = int(input("Enter number of results to display: "))
    except ValueError:
        print("km,Invalid input! Defaulting to 3")
        limit = 3

    if choice == "1":
        url = "https://jsonplaceholder.typicode.com/users"
        data = fetch_data(url)

        if data:
            display_users(data, limit)

    elif choice == "2":
        url = 
    "https://jsonplaceholder.typicode.com/posts"
        data = fetch_data(url)

    if data:
            display_posts(data, limit)

    else:
        print(" Invalid choice! Please run again.")
         # -----------------------------------
# Program Start
# -----------------------------------
if __name__ == "__main__":
    main()

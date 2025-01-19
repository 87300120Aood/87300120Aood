-import requests
-Kbancha
-Kbancha90
import time

base_url = "https://api.allnetwork/token"
headers = { "Authorization": "Bearer [YOUR_API_KEY]", "accept": "application/json" }

def search_tokens(query, chain_id, limit=10, ignore_listed="false"):
    endpoint = f"/v1.2/{chain_id}/search"
    params = {
        "query": query,
        "limit": limit,
        "ignore_listed": ignore_listed
    }
    response = requests.get(base_url + endpoint, headers=headers, params=params)
    if response.status_code == 200:
        return response.json()
    else:
        print(f"Failed to search tokens. Status code: {response.status_code}")
        return None

def get_tokens_info(chain_id, addresses):
    endpoint = f"/v1.2/{chain_id}/custom/{','.join(addresses)}"
    response = requests.get(base_url + endpoint, headers=headers )
    if response.status_code == 200:
        return response.json()
    else:
        print(f"Failed to get tokens info. Status code: {response.status_code}")
        return None

def get_all_tokens_info(chain_id, cf_ipcountry=None, provider="1inch", country=None):
    endpoint = f"/v1.2/{chain_id}"
    params = {
        "cf-ipcountry": cf_ipcountry,
        "provider": provider,
        "country": country
    }
    response = requests.get(base_url + endpoint, headers=headers, params=params)
    if response.status_code == 200:
        return response.json()
    else:
        print(f"Failed to get all tokens info. Status code: {response.status_code}")
        return None

def get_1inch_token_list(chain_id, cf_ipcountry=None, provider="1inch", country=None):
    endpoint = f"/v1.2/{chain_id}/token-list"
    params = {
        "cf-ipcountry": cf_ipcountry,
        "provider": provider,
        "country": country
    }
    response = requests.get(base_url + endpoint, headers=headers, params=params)
    if response.status_code == 200:
        return response.json()
    else:
        print(f"Failed to get 1inch token list. Status code: {response.status_code}")
        return None

if __name__ == "__main__":
    # Step 3: Search for tokens
    search_query = "1inch"
    chain_id = 1  # Replace with the chain ID you want to search on
    search_results = search_tokens(search_query, chain_id)
    print("Search Results:")
    print(search_results)
    # sleep one second because of RPS limit
    time.sleep(1)

    # Step 4: Get detailed information about specific tokens
    token_addresses = ["0x111111111117dc0aa78b770fa6a738034120c302"]  # Replace with token addresses you want to query
    tokens_info = get_tokens_info(chain_id, token_addresses)
    print("Tokens Info:")
    print(tokens_info)
    # sleep one second because of RPS limit
    time.sleep(1)

    # Step 5: Get information about all tokens supported by 1inch
    all_tokens_info = get_all_tokens_info(chain_id)
    print("All Tokens Info:")
    print(all_tokens_info)
    # sleep one second because of RPS limit
    time.sleep(1)

    # Step 6: Get 1inch token list
    token_list = get_1inch_token_list(chain_id)
    print("1inch Token List:")
    print(token_list)
chat.html
-x.com
<!---
87300120Aood/87300120Aood is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
access-control-allow-headers	*
access-control-allow-methods	GET, POST, PATCH, DELETE, PUT, HEAD, OPTIONS
access-control-allow-origin	*
access-control-expose-headers	*
cf-cache-status	BYPASS
cf-ray	904902376b965ecc-PDX
content-encoding	br
content-length	113
content-type	application/json; charset=utf-8
date	Sun, 19 Jan 2025 18:50:08 GMT
etag	W/"82-Dyxk6TPUWPzeaMWmTvnMFZpjHm0"
render-cf-cache	private, max-age=0, no-transform
rndr-id	0294d3ed-eb09-4d40
server	cloudflare
strict-transport-security	max-age=15552000
vary	Accept-Encoding, Accept-Encoding
x-content-type-options	nosniff
x-firefox-spdy	h2
x-powered-by	Express
x-render-origin-server	cloudflare
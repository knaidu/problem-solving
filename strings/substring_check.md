# Substring check

Given a string s and substring sub, find if it exists.

## Algorithm

1. Compare every char of s with sub, if there is a match increment both pts and proceed
2. If there is no match then reset subPtr and proceed with sPtr.

## Code
```ruby
bool substringExists(string& str, string& substr) {
	int m = str.size();
	int n = substr.size();

	if(m == 0 || n == 0 || m < n)
		return FALSE;

	int j = 0;
	for(int i=0; i<m; i++) {
		int k = i;
		while(str[k].compare(substr[j]) == 0 && j < n) {
			k++; j++;
		}
		if(j == n+1) return TRUE;
		else j = 0;
	}

	return FALSE;
}
```

## Time complexity

O(mn), where m is the length of string s, and n is the lenght of substring sub.

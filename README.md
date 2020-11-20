# Sliding-Windows
An example of a typical sliding window

string minWindow(string s, string t) {
  unodrdered_map<char, int> need, window;
  for (char c : t) need[c]++;
  
  int left = 0, right = 0;
  int valid = 0;
  int start = 0, len = INT_MAX;
  while (right < s.size()) {
    char c = s[right];
    right++;
    if (need.count(c)){
      window[c]++;
      if (window[c] == need[c])
      valid++;
    }
    
    while(valid == need.size()) {
      if (right - left < len) {
        start = left;
        len = right -left;
      }
      char d = s[left];
      left++;
      if (need.count(d)) {
        if (window[d] == need[d])
          valid--;
        window[d]--;
      }
    }
  }
  return len == INT_MAX ? " : s.substr(star, len);

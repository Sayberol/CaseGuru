# CaseGuru
def repeat_substring(s):
  result = ""
  i = 0
  while i < len(s):
    if s[i].isdigit():
      j = i
      while j < len(s) and s[j].isdigit():
        j += 1
      repeat = int(s[i:j])
      i = j
      if s[i] == "{":
        bracket_count = 1
        j = i + 1
        while j < len(s) and bracket_count > 0:
          if s[j] == "{":
            bracket_count += 1
          elif s[j] == "}":
            bracket_count -= 1
          j += 1
        substring = repeat_substring(s[i+1:j-1])
        result += repeat * substring
        i = j
    else:
      result += s[i]
      i += 1
  return result
  
input_string = "ab2{g}3{a2{fg}}"
print(repeat_substring(input_string))

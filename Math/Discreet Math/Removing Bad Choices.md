Given a problem where there's a sequence of random characters, but one must be a certain option, how do you find the possible solutions?

> i.e given a 5 char string of ASCII characters, one must be an @ sign, how many possibilities are there?

1. We know that there are 128 ASCII characters, so we can calculate the number of *unrestricted* possibilities. Its `128^5`
2. However, we **don't** need unrestricted possibilities. We gotta instead subtract all the possibilities opposite of our restriction. If we ""remove"" our @ sign from the set of ASCII characters, we have 127 characters left. So all the possibilities without an @ sign would be `127^5`
3. Our answer finally comes out to `128^5 - 127^5`
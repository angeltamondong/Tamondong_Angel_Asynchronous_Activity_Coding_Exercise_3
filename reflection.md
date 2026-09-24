Conceptual Distinction

i. What error occurred when trying to access atm.__pin directly? Why does Python behave this way?

- Attempting to access atm.__pin directly resulted in an AttributeError. This happens because the double underscore prefix marks __pin as a private attribute, and Python applies name mangling to make such attributes harder to access from outside the class. This is especially useful for sensitive data like a PIN, as it helps guard against accidental viewing, modification, or exposure.

ii. How did using @property let you adjust internal logic or add checks without changing how others use the code?

- The @property decorator lets you access and modify values as if they were regular attributes—for example, using account.balance—while keeping the actual implementation hidden. Even if the real data is stored internally under a different name like _balance, the caller never needs to know those details. You can also include validation in the setter, such as blocking negative balances. Best of all, you can rewrite or improve the internal code later without breaking how people use account.balance; the interface stays exactly the same.

iii. How did the ATM class show abstraction compared to the BankAccount logic underneath?

- The ATM class demonstrates abstraction by concealing the complex details of how the bank account works. Users never interact directly with internal details like _balance or transaction records; instead, they use simple, dedicated methods such as check_balance, perform_deposit, and perform_withdrawal. Everything beyond these basic actions is kept private—changes to underlying data would require proper bank authorization, not direct access—so users only see and use the essential functions they need.

Final Reflection Questions

i. What error occurred when trying to access atm.__pin directly? Why does Python behave this way?

- Accessing atm.__pin directly raised an AttributeError. This happens because __pin is a private attribute, and Python uses name mangling on names starting with double underscores to block easy external access. This design protects sensitive information—like a user’s PIN or personal details—from being accidentally read, modified, or leaked.

ii. How did using @property let you adjust internal logic or add checks without changing how others use the code?

-With @property, you can access the balance as account.balance instead of calling special methods. The real value may be stored internally as _balance, but users don’t need to know that. You can also add rules—such as preventing negative balances—through the setter. Crucially, the way people use account.balance never changes, so you can update the backend logic anytime without disrupting existing code.

iii. How did the ATM class show abstraction compared to the BankAccount logic underneath?

- The ATM class hides the complexity of the BankAccount system from the user. Instead of touching internal variables like _balance or transaction lists, users work only with straightforward methods like checking the balance, depositing, and withdrawing. All other data and operations remain inaccessible, so no one can alter account details directly—just as real users would not have permission to modify bank records without proper authorization.

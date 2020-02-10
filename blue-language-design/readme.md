


# QUICK SAMPLES

## FUNCTION CALL
double(x)
x ~ double
x ~ (_ * 2)


## RECORD TYPE DEF


## RECORD FIELD TYPE DEF


## FUNCTION DEF
double = _ * 2
double(x) = x * 2



# POKER

Suit = field [ Clubs, Diamonds, Hearts, Spades ]
J = 11
Q = 12
K = 13
A = 14
LowA = 1
Rank = field [ range(2, 10), J, Q, K, A ]
MysterySuit = field Suit or Unknown
MysteryRank = field Rank or Unknown
UnknownCard = record { MysterySuit, MysteryRank }
Card = record { Suit, Rank }





# INVOICES

InvoiceNumber = field { MinLength = 3, MaxLength = 100 }
ScannedInvoiceDate = field { MinLength = 3, MaxLength = 20 }
InvoiceDate = field { }
ScannedPurchaseOrderNumber = field { }
ScannedInvoiceAmount = field { }
InvoiceAmount = field { }

Company = record { Code, Name }
Vendor = record { }
PurchaseOrder = record { PONumber, Company, Vendor }


ScannedInvoice = record { InvoiceNumber, ScannedInvoiceDate, ScannedPurchaseOrderNumber }

Invoice = record { InvoiceNumber, InvoiceDate, PurchaseOrder }


HttpPost(Invoice) = 
    -- meh

HttpPut(Invoice)



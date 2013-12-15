Input :

Data.csv        : CSV file that contains data from the stock market
DataFormat.xml  : XML file showing format of data in Data.xml
                  looks like this :

                ..   <field-n>
                ..       <label>    value   </label>
                ..       <type>     value   </type>
                ..       <formula>  value   </formula>
                ..   </field-n>

Example :
    <field1>
        <label>     Open    </label>
        <type>      float   </type>
        <formula>   native  </formula>
    </field1>
    <field2>
        <label>     High    </label>
        <type>      float   </type>
        <formula>   native  </formula>
    </field2>
    <field3>
        <label>     Change          </label>
        <type>      float           </type>
        <formula>   Open-Close/Open </formula>
    </field2>

Each member of every generation of the GA represents:

    weight of data of a day
        weight of "Open"            price for the day
        weight of "High"            for the day
        weight of "Low"             for the day
        weight of "Close"           for the day
        weight of "Shares Traded"   for the day

    weight of data of next day
        weight of "Open"            price for the day
        weight of "High"            for the day
        weight of "Low"             for the day
        weight of "Close"           for the day
        weight of "Shares Traded"   for the day

    The above entries would come from the DataFormat.xml file

The GA is expected to find weights which would translate
to a buy / sell trigger for a scrip.

Using the rule represented in each set of weights, shares
are bought; these shares are sold once they reach a profit
of <x>
Each child in the GA is scored based on the profit / loss
that it generates. If a profit of <x> is recorded, then the
time required to make the profit determines the score -
quicker the better.

Future Ideas :
    formula of the following kind might have to be allowed
        <formula>   (Open:n)-(Close:n-1)/Open(:n)   </formula>

# contact-class

/**
 * The Contact class implements a contact book entry by storing information personal to
 * various contacts. This serves as the building block for a Contact List.
 *
 * @author Asma Awad
 * @version 1.0
 */
public class Contact implements Comparable<Contact> {
    private String first, last, phone, address, city, state;

    public Contact(String first, String last, String phone, String address, String city, String state) {
        this.first = first;
        this.last = last;
        this.phone = phone;
        this.address = address;
        this.city = city;
        this.state = state;
    }
    public Contact(String first, String last, String phone) {
        this(first, last, phone, "","","");
    }

    //accessor methods

    /**
     * getFirst serves as an accessor method for a Contact's first name
     * @return the first name of a Contact
     */
    public String getFirst() {
        return first;
    }

    /**
     * getLast serves as an accessor method for a Contact's last name
     * @return the last name of a Contact
     */
    public String getLast() {
        return last;
    }

    /**
     * getPhone serves as an accessor method for a Contact's phone number
     * @return the phone number of a Contact
     */
    public String getPhone() {
        return phone;
    }

    /**
     * getAddress serves as an accessor for a Contact's address
     * @return the address of a Contact
     */
    public String getAddress() {
        return address;
    }

    /**
     * getCity serves as an accessor for a Contact's city
     * @return the city of a contact
     */
    public String getCity() {
        return city;
    }

    /**
     * getState serves as an accessor for a Contact's State
     * @return the state of a Contact
     */
    public String getState() {
        return state;
    }

    /**
     * update allows one to update their contact information
     * @param first the Contact's updated first name
     * @param last the Contact's updated last name
     * @param phone the Contact's updated phone number
     * @param address the Contact's updated address
     * @param city the Contact's updated city
     * @param state the Contact's updated state
     */
    public void update(String first, String last, String phone, String address, String city, String state) {
        this.first = first;
        this.last = last;
        this.phone = phone;
        this.address = address;
        this.city = city;
        this.state = state;
    }

    /**
     * compareTo allows Contacts to be comparable by their last names' natural order,
     * but in the case that the last names are the same, it uses the first names instead
     *
     * @param other the Contact that the Contact the method being called on is compared to
     * @return a positive number, negative number, or zero based on the alphabetical ordering of the
     * strings relative to each other as determined by Java's builtin compareTo method
     */
    public int compareTo(Contact other) {
        int result = last.compareTo(other.last);
        if (result == 0)
            return first.compareTo(other.first);
        else
            return result;
    }

    /**
     * equals determines whether or not two Contacts are equal based on the compareTo method above
     * @param obj an object to be compared to the Contact the method is called on
     * @return true or false depending on the compareTo method
     */
    public boolean equals(Object obj) {
        //ensure that the Object is a Contact before comparing the two
        if (!(obj instanceof Contact))
            return false;
        //cast the Object to a Contact if it reaches past the instanceof check
        Contact other = (Contact) obj;
        return this.compareTo(other) == 0;
    }

    /**
     * toString provides a formatted representation of a Contact
     * @return a formatted String representing all Contact information
     */
    public String toString() {
        String str1 = first + " " + last + "\t\t" + "Phone number: " + phone;
        String str2 = "\n" + address + "\n" + city + ", " + state;

        //in the case that no address, city, & state are provided, toString won't print an extra comma + newline characters
        if (address.equals("") && city.equals("") && state.equals(""))
            return str1;
        return str1 + str2;
    }
}

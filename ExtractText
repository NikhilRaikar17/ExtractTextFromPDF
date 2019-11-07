mport PyPDF2
import operator

def pdfparser(pdffiles):
    fullText = []
    for pdffile in pdffiles:
        print(pdffile)
        with open(pdffile, mode='rb') as pdfFileObj :
            print("Opening pdf file named:", pdffile)
            documents = fullText
            pdfReader = PyPDF2.PdfFileReader(pdfFileObj)

            # Put all the text into one single variable.
            details_page = []
            for each in range(pdfReader.numPages):
                pageObj = pdfReader.getPage(each)
                variable = pageObj.extractText()
                details_page.append(variable)
            print(details_page)

            # Create a example words list(Please add all the related keywords needed)
            words_list = ["Abstract", "Introduction", "Conclusion","ABSTRACT"]
            #print("There are", len(words_list), "in the words list")
            str = " "
            details = str.join(details_page)
            details.replace(" ", "\n")
            #print(details)
            words = details.split()
            #print(words)
            place = []

            # Enumerate and create a rank between the keywords.
            for c, a in enumerate(words):
                for b in words_list:
                    if b == a and b not in place:
                        print(details.find("{}".format(b)))
                        place.append(details.find("{}".format(b)))
                    elif b not in words:
                        words_list.remove(b)
                        print("The word", b, "was not found in the pdf file")

            final_array = list(zip(words_list, place))
            final_array.sort(key=operator.itemgetter(1))
            print(final_array)

            print("Extracting the relevant texts from pdf")
            if len(final_array)>1:
                listint = final_array[0]
                print(listint)
                list2int = final_array[1]
                counter = 0

                for each in (final_array):
                    if counter < len(final_array) - 2:
                        new = (details.split(listint[0])[1].split(list2int[0])[0])
                        #new = sent_tokenize(new)
                        print(listint[0], ":", [''.join(new)])
                        documents.append(new)
                        counter = counter + 1
                        listint = final_array[0 + counter]
                        list2int = final_array[1 + counter]

                    elif counter < len(final_array) - 1:
                        new = (details.split(final_array[counter][0])[1].split(final_array[counter + 1][0])[0])
                        #new = sent_tokenize(new)
                        documents.append(new)
                        print(final_array[counter][0], ":", [''.join(new)])
                        print(" ")
                        counter = counter + 1
                    else:
                        new = (details.split(final_array[counter][0])[1])
                        #new = sent_tokenize(new)
                        documents.append(new)
                        print(final_array[counter][0], ":", [''.join(new)])
                        print(" ")
            else:
                for each in (final_array):
                    new = (details.split(each[0])[1])
                    documents.append(new)
                    print(each[0], ":", [''.join(new)])
                    print(" ")

    return documents


if __name__=="__main__":
    pdfparser(["e.pdf","r.pdf"])
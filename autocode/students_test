package coverage

import (
	"errors"
	"fmt"
	"os"
	"reflect"
	"sort"
	"testing"
	"time"
	//"github.com/stretchr/testify/assert"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
func (p Person) String() string {
	return fmt.Sprintf("%s-%s %s", p.firstName, p.lastName,p.birthDay)
}
func TestSortPerson(t *testing.T){
	type test struct {
        ipeople People
        epeople People
    }

    tests := []test{
        {
			ipeople: People{
			{firstName: "FTest1",lastName: "LTest1",birthDay: time.Date(1982, 1, 2, 0, 0, 0, 0, time.UTC)},
			{firstName: "FTest2",lastName: "LTest2",birthDay: time.Date(1986, 1, 2, 0, 0, 0, 0, time.UTC)},
			{firstName: "FTest3",lastName: "LTest3",birthDay: time.Date(1986, 1, 2, 0, 0, 0, 0, time.UTC)},
			{firstName: "FTest3",lastName: "LTest4",birthDay: time.Date(1986, 1, 2, 0, 0, 0, 0, time.UTC)},
		},
           epeople:  People{
			{firstName: "FTest2",lastName: "LTest2",birthDay: time.Date(1986, 1, 2, 0, 0, 0, 0, time.UTC)},
			{firstName: "FTest3",lastName: "LTest3",birthDay: time.Date(1986, 1, 2, 0, 0, 0, 0, time.UTC)},   
			{firstName: "FTest3",lastName: "LTest4",birthDay: time.Date(1986, 1, 2, 0, 0, 0, 0, time.UTC)},
			{firstName: "FTest1",lastName: "LTest1",birthDay: time.Date(1982, 1, 2, 0, 0, 0, 0, time.UTC)},
		 },
	},
    }

	for i, tc := range tests {
        sort.Sort(tc.ipeople)
		if !reflect.DeepEqual(tc.epeople, tc.ipeople) {
            t.Fatalf("test %d: expected: %v, got: %v", i+1, tc.epeople, tc.ipeople)
        }
    }
    }
func TestStringMatrix(t *testing.T){
	type test struct {
        input string
		rows [][]int
		cols [][]int
		set bool
		err error
    }

    tests := []test{
        {
			input: "1234 567 890 1\n1234 567 890 1",
			rows: [][]int{
				{1234, 567, 890 ,1},
				{1234, 567, 890 ,1},
			},
			cols: [][]int{
				{1234,1234},
				{567,567},
				{890,890},
				{1,1},
			},
			set: true,
			err: nil,
	  },
	  {
		input: "1234 567 890 1\n1234 567 890",
		err: errors.New("Rows need to be the same length"),
	},
	{
		input: "Apple",
		err: errors.New("strconv.Atoi: parsing \"Apple\": invalid syntax"),
	},
  }
    

	for i, tc := range tests {
        m,err:=New(tc.input)
		if(err == nil){
		rows:=m.Rows()
		if !reflect.DeepEqual(tc.rows, rows){
			t.Fatalf("test %v: expected: %v, got: %v", i+1, tc.rows,rows)
		}
		cols:=m.Cols()
		if !reflect.DeepEqual(tc.cols, cols){
			t.Fatalf("test %v: expected: %v, got: %v", i+1, tc.cols,cols)
		}
		set:=m.Set(1,3,999)
		if !set{
			t.Fatalf("test %v: expected: %v, got: %v", i+1, tc.set,set)
		}
		set=m.Set(2,3,999)
		if set{
			t.Fatalf("test %v: expected: %v, got: %v", i+1, tc.set,set)
		}
	   }
		if err!=nil && err.Error() != tc.err.Error() {
			t.Fatalf("test %v: Error expected %v Error happened %v ", i+1, tc.err,err)
		}
	
 }	
	
}


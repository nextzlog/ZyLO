# zylo
--
    import "github.com/nextzlog/zylo"

provides the zLog programming interface to the Go language. Copyright (C) 2020
JA1ZLO.

## Usage

```go
const (
	CW    = 0
	SSB   = 1
	FM    = 2
	AM    = 3
	RTTY  = 4
	OTHER = 5
)
```
mode enumeration.

```go
const (
	M1_9  = 0
	M3_5  = 1
	M7    = 2
	M10   = 3
	M14   = 4
	M18   = 5
	M21   = 6
	M24   = 7
	M28   = 8
	M50   = 9
	M144  = 10
	M430  = 11
	M1200 = 12
	M2400 = 13
	M5600 = 14
	G10UP = 15
)
```
band enumeration.

```go
const INI = "zlog.ini"
```
path to zlog.ini.

```go
const QBYTES = 256
```
QSO struct size.

```go
var DeleteQSO func(qso *QSO)
```
a bridge function to delete a QSO.

```go
var HookButton func(name string)
```
a bridge function to add button handler.

```go
var HookEditor func(name string)
```
a bridge function to add editor handler.

```go
var InsertQSO func(qso *QSO)
```
a bridge function to insert a QSO.

```go
var UpdateQSO func(qso *QSO)
```
a bridge function to update a QSO.

#### func  CapturePanic

```go
func CapturePanic()
```
captures a panic and display the detailed information of the panic.

#### func  GetINI

```go
func GetINI(section, key string) (value string)
```
gets a specified value from zlog.ini

#### func  Notify

```go
func Notify(msg string, args ...interface{})
```
displays a message as a toast.

#### func  SetINI

```go
func SetINI(section, key, value string) (err error)
```
sets a specified value into zlog.ini

#### type QSO

```go
type QSO struct {
	ID   uint32
	Mode byte
	Band byte
	Pow1 byte

	Score byte

	Dupe bool

	TxID byte
	Pow2 uint32
}
```

a single QSO data.

#### func  ToQSO

```go
func ToQSO(ptr uintptr) (qso *QSO)
```
converts a raw pointer into a QSO.

#### func (*QSO) Delete

```go
func (qso *QSO) Delete()
```
deletes a QSO in zLog.

#### func (*QSO) Dump

```go
func (qso *QSO) Dump(locale *time.Location) []byte
```
converts a QSO into a binary data.

#### func (*QSO) GetCall

```go
func (qso *QSO) GetCall() string
```
extracts the contacted station's callsign.

#### func (*QSO) GetMul1

```go
func (qso *QSO) GetMul1() string
```
extracts the 1st multiplier.

#### func (*QSO) GetMul2

```go
func (qso *QSO) GetMul2() string
```
extracts the 2nd multiplier.

#### func (*QSO) GetName

```go
func (qso *QSO) GetName() string
```
extracts the operator's name.

#### func (*QSO) GetNote

```go
func (qso *QSO) GetNote() string
```
extracts the QSO notes.

#### func (*QSO) GetRcvd

```go
func (qso *QSO) GetRcvd() string
```
extracts the received serial number.

#### func (*QSO) GetSent

```go
func (qso *QSO) GetSent() string
```
extracts the transmitted serial number.

#### func (*QSO) GetTime

```go
func (qso *QSO) GetTime(zone *time.Location) time.Time
```
extracts the operation time from the QSO.

#### func (*QSO) Insert

```go
func (qso *QSO) Insert()
```
inserts a QSO to zLog.

#### func (*QSO) SetCall

```go
func (qso *QSO) SetCall(value string)
```
extracts the contacted station's callsign.

#### func (*QSO) SetMul1

```go
func (qso *QSO) SetMul1(value string)
```
sets the 1st multiplier.

#### func (*QSO) SetMul2

```go
func (qso *QSO) SetMul2(value string)
```
sets the 2nd multiplier.

#### func (*QSO) SetName

```go
func (qso *QSO) SetName(value string)
```
extracts the operator's name.

#### func (*QSO) SetNote

```go
func (qso *QSO) SetNote(value string)
```
extracts the QSO notes.

#### func (*QSO) SetRcvd

```go
func (qso *QSO) SetRcvd(value string)
```
extracts the received serial number.

#### func (*QSO) SetSent

```go
func (qso *QSO) SetSent(value string)
```
extracts the transmitted serial number.

#### func (*QSO) Update

```go
func (qso *QSO) Update()
```
updates a QSO in zLog.

#### type QxSL

```go
type QxSL struct {
}
```

reference to qxsl.exe

#### func  LoadQxSL

```go
func LoadQxSL(bytes []byte) (qxsl *QxSL, err error)
```
loads qxsl.exe from the byte array.

#### func (*QxSL) Close

```go
func (exe *QxSL) Close() error
```
releases resources for qxsl.exe.

#### func (*QxSL) Filter

```go
func (exe *QxSL) Filter() (filter string, err error)
```
calls qxsl.exe to obtain filter string for a file dialog.

#### func (*QxSL) Format

```go
func (exe *QxSL) Format(source, target, format string) error
```
calls qxsl.exe to format the specified log into another format.

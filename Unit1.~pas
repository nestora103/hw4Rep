unit Unit1;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls;

type
  TForm1 = class(TForm)
    btn1: TButton;
    edt1: TEdit;
    edt2: TEdit;
    lbl1: TLabel;
    lbl2: TLabel;
    edt3: TEdit;
    lbl3: TLabel;
    edt4: TEdit;
    lbl4: TLabel;
    mmo1: TMemo;
    procedure btn1Click(Sender: TObject);
  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.dfm}

//==============================================================================
//Jтбросим вещ. часть
//==============================================================================
function DelV(s:string):string;
var
  strP,strM:string;
  strR:string;
  i: integer;
  bool:Boolean;
  count:integer;
begin
  if AnsiPos('E',s)<>0 then
  begin
    strP:='';
    strM:='';
    bool:=False;
    count:=0;
    i:=1;
    while (s[i]<>'E') do
    begin
      if (bool) then
      begin
        Inc(count);
      end;
      if s[i]='.' then
      begin
        bool:=True;
      end;
      strP:=strP+s[i];
      Inc(i);
    end;

    i:=i+2;
    while i<=length(s) do
    begin
      strM:=strM+s[i];
      Inc(i);
    end;

    if StrToInt(strM)>count then
    begin
      strR:='';
      for i:=1 to Length(strP) do
      begin
        if strP[i]<>'.' then
        begin
          strR:=strR+strP[i];
        end;
      end;
      strP:=strR;
    end;
  end
  else
  begin
    strP:=s;
  end;
  
  result:=strP;
end;
//==============================================================================




//==============================================================================
//Перевернуть строку
//==============================================================================
function ReverseNum(num:{cardinal}extended): {Cardinal}extended;
var
  i: integer;
  s: string;

  res:string;
begin
  s:={IntToStr(num)}floatToStr({Int(num)}num);

  s:=DelV(s);

  res := '';
  if Trim(s) <> '' then
  begin
    for i := Length(s) downto 1 do
    begin
      res := res + s[i];
    end;
  end
  else
  begin
    Result :=0;
  end;
  Result:=StrToFloat(res);
end;
//==============================================================================


//==============================================================================
//Функция определния является ли переданное число полиндромом
//==============================================================================
function PoliNumTest(num:{cardinal}extended):Boolean;
var
  bool:Boolean;
  numStr:string;
begin
  bool:=False;
  numStr:=floatToStr(num);
  numStr:=DelV(numStr);
  num:=StrToFloat(numStr);
  //Определим четное ли количество символов в строке-числе
  if Length(numStr)>2 then
  begin
    //количество символов в числе четное
    if num*1000=ReverseNum(num)*1000 then
    begin
      //число является полиндпромом
      bool:=True;
    end;
  end;
  result:=bool;
end;
//==============================================================================


//==============================================================================
//
//==============================================================================
function TestNumber(num:Extended{Cardinal};repMax:Cardinal):Boolean;
var
  bool:Boolean;
  i:Integer;
  sum:{Cardinal}Extended;
begin
  bool:=false;
  sum:=num+ReverseNum(num);
  for i:=1 to repMax do
  begin
    if PoliNumTest(sum) then
    begin
      form1.mmo1.Lines.Add('Число:'+floatTostr(num)+' #Прохода:'+intTostr(i)+
      ' Полиндром:'+floatTostr(sum));
      bool:=true;
      Break;
    end;
    //Form1.mmo1.Lines.Add(IntToStr(i)+' '+floatToStr(sum));
    sum:=sum+ReverseNum(sum);
  end;
  result:=bool;
end;
//==============================================================================


procedure TForm1.btn1Click(Sender: TObject);
var
  i:Cardinal;
  startN:Cardinal;
  finishN:Cardinal;
  repeatMax:Cardinal;
  repeatCount:Cardinal;
  countNotPMNum:Cardinal;
begin
  countNotPMNum:=0;
  repeatCount:=0;
  //от
  startN:=StrToInt(Form1.edt1.Text);
  //до
  finishN:=StrToInt(Form1.edt2.Text);
  //количество повторений
  repeatMax:=StrToInt(Form1.edt3.Text);
  for i:=startN to finishN do
  begin
    if not(TestNumber(i,repeatMax)) then
    begin
      //число за 50 проходов не полиндром
      form1.mmo1.Lines.Add(IntToStr(i));
      form1.edt4.Text:=intTostr(countNotPMNum);
      Inc(countNotPMNum);
    end;
  end;
  form1.edt4.Text:=intTostr(countNotPMNum);
end;

end.

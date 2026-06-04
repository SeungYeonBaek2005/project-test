#include <iostream>
#include <stdlib.h>
#include <time.h>
// 주제 마리오 루이지 rpg

using namespace std;

class character
{
public:
	character() {};
	void get_attack(string _name, int damage);
	void use_fb(string _name, int _use_fb);
	void set(string _name);
	void g_set(string _name);
	int check_hp() { return hp; };
	int check_fb() { return fb; };

protected:
	string name;
	int hp = 0;
	int fb = 0;
};

int main()
{
	character mario; // 마리오
	character luigi; // 루이지
	character Goomba1; // 굼바1
	character Goomba2; // 굼바2

	string name[2] = { "마리오","루이지" };
	string g_name[2]{ "굼바1","굼바2" };
	int num, num2;

	srand(time(NULL));

	// 마리오 루이지 캐릭터 체력 설정
	mario.set(name[0]);
	luigi.set(name[1]);
	// 굼바 캐릭터들 체력 설정
	Goomba1.g_set(g_name[0]);
	Goomba2.g_set(g_name[1]);
	cout << endl;

	
	while (1)
	{
		// 마리오 루이지 턴
		for (int i = 0; i < 2; i++)
		{
			if (mario.check_hp() == 0 && i == 0) // 마리오가 죽었을 때 턴 자동으로 넘기는 기능
			{
				i++;
			}
			else if (luigi.check_hp() == 0 && i == 1) // 루이지가 죽었을 때 턴 자동으로 넘기는 기능
			{
				break;
			}
			
			cout <<"(" << name[i] << ") 턴" << endl;
			cout << "1. 점프 : 데미지 4 FB소모 0\n";
			cout << "2. 해머 : 데미지 6 FB소모 2\n";
			cout << "둘 중 (공격방법)을 골라주세요. (숫자 입력)\n";
			cin >> num;
			if (num < 1 || num > 2) // 그외에 숫자를 입력했을 때
			{
				cout << "1,2중 숫자 입력해주세요.\n\n";
				i--;
				continue;
			}
			else if (mario.check_fb() < 2 && num==2 && i==0 || luigi.check_fb()<2 && num==2 && i==1) // FB가 부족할 때
			{
				cout << "{FB가 부족합니다.}\n\n";
				i--;
				continue;
			}

			for (int i = 0; i < 2; i++) // 굼바 생존 여부 보여주기
			{
				if (Goomba1.check_hp() == 0 && i == 0 || Goomba2.check_hp() == 0 && i == 1)
				{
					cout << "(" << g_name[i] << ") 쓰러짐\n";
				}
				else
				{
					cout << "(" << g_name[i] << ") 살아 있음\n";
				}
			}
			cout << "(적)을 선택해주세요 (숫자 입력)\n";
			cin >> num2;
			if (num2 < 1 || num2 > 2) // 그 외에 숫자를 입력했을 경우
			{
				cout << "1,2중 숫자 입력해주세요.\n\n";
				i--;
				continue;
			}
			else if (Goomba1.check_hp() == 0 && num2==1) // 쓰러진 적의 숫자를 입력했을 경우
			{
				cout << g_name[0] << "는 쓰러졌습니다. 다시 골라주세요.\n\n";
				i--;
				continue;
			}
			else if (Goomba2.check_hp() == 0 && num2==2) // 쓰러진 적의 숫자를 입력했을 경우
			{
				cout << g_name[1] << "는 쓰러졌습니다. 다시 골라주세요.\n\n";
				i--;
				continue;
			}

			// 공격 방법 선택
			switch (num)
			{
			case 1: // 점프 공격
				// 적 선택
				switch (num2)
				{
				case 1: // 굼바1

					Goomba1.get_attack(name[i], 4);
					break;
				case 2: // 굼바 2

					Goomba2.get_attack(name[i], 4);
					break;
				}
				break;
			case 2: // 해머 공격
				// 적 선택
				switch (num2)
				{
				case 1: // 굼바 1
					Goomba1.get_attack(name[i], 6);
					if (i == 0)
					{
						mario.use_fb(name[0], 2);
					}
					else if (i == 1)
					{
						luigi.use_fb(name[1], 2);
					}
					break;
				case 2: // 굼바 2
					Goomba2.get_attack(name[i], 6);
					if (i == 0)
					{
						mario.use_fb(name[0], 2);
					}
					else if (i == 1)
					{
						luigi.use_fb(name[1], 2);
					}
					break;
				}
				break;
			}
			if (Goomba1.check_hp() == 0 && Goomba2.check_hp() == 0) // 굼바가 다 쓰러졌을 경우
			{
				break;
			}
		}
		if (Goomba1.check_hp() == 0 && Goomba2.check_hp() == 0) // 굼바가 다 쓰러졌을 경우
		{
			cout << "마리오 루이지가 전투에서 승리했다!!!\n";
			break;
		}
		
		getchar(); // 아무 키 누르면 자동으로 넘어가는 기능
		srand(time(NULL));
		int num2;
		for (int i = 0; i < 2; i++)
		{
			cout << ">> 다음 대사를 넘길려면 아무 키 눌러주세요.\n";
			getchar(); // 아무 키 누르면 자동으로 넘어가는 기능
			if (Goomba1.check_hp() == 0 && i == 0)
			{
				i++;
			}
			else if (Goomba2.check_hp() == 0 && i == 1)
			{
				break;
			}

			num = rand() % 2; // 공격 방법 고르기 랜덤
			num2 = rand() % 2; // 공격 상대 고르기 랜덤
			switch (num)
			{
			case 0: // 1공격
				switch (num2)
				{
				case 0: // 마리오
					if (mario.check_hp() == 0) // 마리오가 죽었을 경우
					{
						luigi.get_attack(g_name[i], 3);
						break;
					}
					mario.get_attack(g_name[i], 3);
					break;
				case 1: // 루이지
					if (luigi.check_hp() == 0) // 루이지가 죽었을 경우
					{
						mario.get_attack(g_name[i], 3);
						break;
					}
					luigi.get_attack(g_name[i], 3);
					break;
				}
				break;
			case 1: // 2 공격
				switch (num2)
				{
				case 0: // 마리오
					if (mario.check_hp() == 0) // 마리오가 죽었을 경우
					{
						luigi.get_attack(g_name[i], 6);
						break;
					}
					mario.get_attack(g_name[i], 6);
					break;
				case 1: // 루이지
					if (luigi.check_hp() == 0) // 루이지가 죽었을 경우
					{
						mario.get_attack(g_name[i], 6);
						break;
					}
					luigi.get_attack(g_name[i], 6);
					break;
				}
				break;
			}
			if (mario.check_hp() == 0 && luigi.check_hp() == 0)
			{
				break;
			}
		}
		cout << ">> 다음 대사를 넘길려면 아무 키 눌러주세요.\n";
		getchar(); // 아무 키 누르면 자동으로 넘어가는 기능
		if (mario.check_hp() == 0 && luigi.check_hp() == 0) // 마리오 루이지가 졌을 경우
		{
			cout << "마리오 루이지는 쓰러졌다.\n";
			cout << "good night\n";
			break;
		}
	}
		
	
		
	return 0;
}


// 마리오 루이지 캐릭터 체력 설정 함수
void character::set(string _name)
{
	name = _name;
	hp = 25;
	fb = 2;
	cout << name << " 체력 설정 완료\n";
}

// 적 캐릭터 체력 설정 함수
void character::g_set(string _name)
{
	name = _name;
	hp = 50;
	fb = 0;
	cout << name << " 체력 설정 완료\n";
}

// 공격 함수
void character::get_attack(string _name, int damage)
{
	hp -= damage;
	cout << "[" << _name << "]는 [" << name << "] 에게 (" << damage << ")데미지를 입혔다.\n";
	
	if (hp <= 0)
	{
		hp = 0;
		cout << "남은 " << name << " 체력 (" << hp << ")" << endl;
		cout << "(" << name << "은 쓰러졌다.)\n\n";
	}
	else
	{
		cout << "남은 " << name << " 체력(" << hp << ")" << endl << endl;
	}
}

// FB 사용 함수
void character::use_fb(string _name, int _use_fb)
{
	fb -= _use_fb;
	cout << "(" << _use_fb << ")FB 사용\n";
	if (fb < 0)
	{
		fb = 0;
	}
	cout << "남은 ["<<_name<< "]의 FB (" << fb << ")" << endl << endl;
}

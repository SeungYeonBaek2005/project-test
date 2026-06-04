#include <iostream>
#include <stdlib.h>
#include <time.h>

using namespace std;
// 페이퍼마리오 천년의 문

class character
{
public:
	character()
	{
		cout << "캐릭터 생성" << endl;
	};

protected:
	int hp;
	int fb;
};

// 마리오 캐릭터 클래스
class mario :public character
{
public:
	mario()
	{
		hp = 25;
		fb = 15;
		cout << "마리오 체력 : " << hp << endl;
		cout << "마리오 FB : " << fb << endl;
		cout << "마리오 체력 설정 완료\n";
	};
	void get_attack(int damage);
	void use_fb(int use_fb);
	int get_hp() { return hp; };
	int get_fb() { return fb; };
};

// 굼바 클래스
class monster :public character
{
public:
	monster()
	{
		hp = 50;
		fb = 10;
		cout << "굼벨라 체력 : " << hp << endl;
		cout << "굼벨라 체력 설정 완료\n";
	}
	void get_attack(int damage);
	void use_fb(int use_fb);
	int get_hp() { return hp; };
};

int main()
{
	mario mario;
	monster goomba;
	int num, ans;
	int a;

	srand(time(NULL));
	cout << "(계속 진행하려면 아무 키 눌러주세요.)\n";
	getchar();

	while (1)
	{
		cout << "공격 1,2,3중 하나를 입력해주세요." << endl;
		cin >> num;

		if (mario.get_fb() < 5 && num == 3 || mario.get_fb() < 3 && num == 2)
		{
			cout << "FB가 부족합니다.\n";
			continue;
		}

		while (1)
		{
			cout << "정말 " << num << "로 하시겠습니까?" << endl;
			cout << "예 1 아니요 2\n";
			cin >> ans;
			if (ans == 1 || ans == 2)
			{
				break;
			}
			else
			{
				cout << "1,2중 숫자 하나 입력해주세요.\n";
				continue;
			}
		}
		if (ans == 2)
		{
			continue;
		}

		switch (num)
		{
		case 1:
			goomba.get_attack(5);
			mario.use_fb(0);
			break;
		case 2:
			goomba.get_attack(10);
			mario.use_fb(3);
			break;
		case 3:
			goomba.get_attack(15);
			mario.use_fb(5);
			break;
		}
		if (0 == goomba.get_hp())
		{
			cout << "굼벨라가 쓰러졌다.\n";
			cout << "마리오가 승리했다.\n";
			break;
		}
		cout << "(계속 진행하려면 아무 키 눌러주세요.)\n";
		getchar();
		getchar();

		a = rand() % 2+1;

		switch (a)
		{
		case 1:
			mario.get_attack(5);
			break;
		case 2:
			mario.get_attack(10);
			break;
		}
		if (0 == mario.get_hp())
		{
			cout << "마리오가 쓰러졌다.\n";
			cout << "마리오가 패배했다.\n";
			break;
		}
		cout << "(계속 진행하려면 아무 키 눌러주세요.)\n";
		getchar();
	}

	return 0;
}

// 마리오 공격 함수
void mario::get_attack(int damage)
{
	hp -= damage;
	if (hp < 0)
	{
		hp = 0;
	}
	cout << "마리오는 " << damage << " 데미지를 입었다.\n";
	cout << "마리오 남은 체력 : " << hp << endl;
}

// 마리오 fb 사용 함수
void mario::use_fb(int use_fb)
{
	fb -= use_fb;
	if (fb < 0)
	{
		fb = 0;
	}
	cout << "마리오 남은 FB : " << fb << endl;
}

// 굼바 공격 함수
void monster::get_attack(int damage)
{
	hp -= damage;
	if (hp < 0)
	{
		hp = 0;
	}
	cout << "굼벨라 " << damage << " 데미지를 입었다.\n";
	cout << "굼벨라 남은 체력 : " << hp << endl;
}
